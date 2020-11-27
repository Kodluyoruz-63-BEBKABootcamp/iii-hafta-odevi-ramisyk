 - [x] .Net kodu nedir ve nasıl derlenir?
 - [x] Roslyn compiler ne işe yarar?
 - [ ] Restful servisler nasıl çalışır? Alternatifleri nelerdir ve nasıl çalışırlar?
 - [x] Extension method nedir? Nasıl yazılır?
 - [x] MVC'nin alternatifleri nelerdir?
 - [x] Architectural pattern nedir? Neden ihtiyaç duyuyoruz?
 - [x] ViewData, ViewBag, TempData farkları nelerdir? Çalıştığımız proje üzerinde başka bir branch açarak bunları deneyiniz?
 
# .NET kodu nedir ve nasıl derlenir?
.NET Framework, Microsoft tarafından geliştirilen farklı ortamlar için kullanılabilen bir uygulama geliştirme platformudur. Verimliliği yüksek, standartlara uygun ve çoklu dil desteği bulunan bir platformdur. 

Hazırlanan .NET projesi üzerinde derlenme işlemi başladığında yazılan kod derleyici tarafından MSIL (Microsoft Intermediate Language) diline dönüştürülür. MSIL, programlama dili ile makine dili arasında bir ara dil olarak kullanılır. Bu işlem sonucunda proje MSIL bir exe dosyasına dönüştürülür. Oluşturulan exe çalışması için JIT (Just-In-Time) Compiler ile yeniden derlenmesi ve bilgisayarın anlayacağı makine diline çevrilmesi gerekmektedir. JIT derleyicisinde çalıştırılacak olan metot çalışma anında derlenerek işleme girer, bütün metotlar başlangıçta değil çalışma anında derlenir [[1](https://bidb.itu.edu.tr/seyir-defteri/blog/2013/09/06/.net-framework), [2](https://youtu.be/MNywsguVPsc)].
# Roslyn compiler ne işe yarar?
.NET Compiler Platform ana görevi ("Roslyn"), C# ve Visual Basic derleyicilerini açıyor ve araçların ve geliştiricilerin zengin bilgi derleyicileri, programlarla paylaşmasına izin verir.  Kod analizi araçları kod kalitesini geliştirir ve kod oluşturucuları uygulama oluşturma konusunda yardımcı olur.  Araçların daha akıllı bir şekilde yararlanabileceği için, yalnızca derleyicilerin sahip olduğu derin kod bilgisine daha fazla ve daha fazlasına erişmesi gerekir.  Sabit bir çevirmenin (ve nesne kodu içindeki kaynak kodu) değil, Roslyn derleyicileri, araçlarınızdaki ve uygulamalarınızda kod ile ilgili görevler için kullanabileceğiniz API 'ler sunar [[3](https://docs.microsoft.com/tr-tr/visualstudio/extensibility/dotnet-compiler-platform-roslyn-extensibility?view=vs-2019)].

# Extension method nedir? Nasıl yazılır?
Extension method mevcut sınıf ve yapılar üzerinde değişiklik yapmadan genişletilmiş metot yazma işlemini sağlar.

Extension method sınıfı tanımlanırken *public static* olarak tanımlanmalıdır. Metot parametresinde  hangi değişken tipi ile çalışılacağı *this* kelimesi ile belirtilmelidir [[4](https://medium.com/@serkan22789/c-extension-method-nedir-16dde50f9630)]. 

# MVC’nin alternatifleri nelerdir?
* **HMVC (Hierarchical Model-View-Controller):**  
Bir sayfa için bir, gezinme için bir tane ve sayfadaki içerik için ayrı bir MVC yapısı oluşturulabilir. bu yapı ile yeniden kullanılabilir widget'lar oluşturulmasına izin verdiği için karmaşık sayfaların yapılandırılmasını kolaylaştırır.
* **MVVM (Model-View-ViewModel):**
MVC'de, View'in presentation and presentation data logic işlemlerini yapmasının kötü bir durum olmasıyla ortaya çıkan bir modeldir. Render işlemlerinde verilerle ilgilenme durumunda bir fark oluşur. Bu fark sayesinde MVVM'de View ikiye bölünür. Render View'da oluşurken veri işlemleri ViewModel'da gerçekleşir.
* **MVP (Model View Presenter):**
MVC'de Controller'ın kullanıcı etkileşimini engellemesi ve View render verisine sahiptir. MVP'de View, pasif görünümden sorumludur ve Modele bağlanmaz, sadece kendisine verilen verileri işler. Ancak Controller gibi kullanıcı etkileşim olaylarını da alır. MVP'de kullanıcıya gösterilen tek şey View'dır.
* **MVA (Model View Adapter):**
Model ve View birbirleriyle asla iletişime geçmez *Adapter* üzerinden veri iletişimi sağlanır.
* **PAC (Presentation Abstraction Control):**
Abstraction bileşeni verileri alır ve işler, Presentation bileşeni verilerin görsel ve işitsel sunumunu biçimlendirir ve Control bileşeni, diğer iki bileşen arasındaki kontrol akışı ve iletişim gibi şeyleri ele alır.
* **RMR (Resource-Method-Representation):**

* **ADR (Action-Domain-Responder):**
RMR ile çok benzerlik göstermektedir. 
*Action:* Method, 
*Resource:* Domain
*Representation:* Responder [[5](https://blog.ircmaxell.com/2014/11/alternatives-to-mvc.html)].

# Architectural pattern nedir? Neden ihtiyaç duyuyoruz?
Belirli bir bağlamda yazılım mimarisinde yaygın olarak ortaya çıkan bir soruna genel, yeniden kullanılabilir bir çözümdür. Belirtilen modeller, bilgisayar donanımı performans sınırlamaları, yüksek kullanılabilirlik ve bir işteki risklerin en aza indirilmesi gibi yazılım mühendisliği alanındaki çeşitli sorunları ele alır [[6](https://en.wikipedia.org/wiki/Architectural_pattern)]. 

# ViewData, ViewBag, TempData farkları nelerdir?
**ViewBag , ViewData ve TempData** **asp.net mvc** nesnelerini  küçük boyutlardaki verilerimizi *Controller* dan *View* kısmına aktarmak için kullanırız.

**ViewData ve ViewBag**  aynı çalışma mantığına sahiptir ancak ViewData  ASP.NET MVC, ASP.NET MVC 2 ve ASP.NET MVC 3 de çalışmaktadır. Fakat ViewBag ASP.NET MVC 3 ile birlikte gelen yeni ve run time içerisinde oluşan dinamik bir ASP.NET MVC 3 nesnesidir. ViewData kullanımında köşeli parentez içerisine içerisine yazılan anahtar kelime sayesinde diğer ViewData lardan ayrılmış olur. ViewData nesneside birden fazla farklı nesne ayırmasını ViewDataDictionary sınıfı aracılıyla, "key/value" syntax sayesinde çözümlemiş olur.

**TempData** herhangi Controller'dan oluşturulmuş olan veriyi View'ler arasında taşınmasında veya tek bir View içerisinde elimizdeki veriyi ekran çıktısı olarak görüntülenmesinde görev alır [[7](http://www.aspmvcnet.com/tr/m/razor/viewbag-viewdata-ve-tempdata-asp-net-mvc-3-kullanimi-ve-farklari.html)].

# Kaynaklar
1. İnternet: .NET Framework
https://bidb.itu.edu.tr/seyir-defteri/blog/2013/09/06/.net-framework
2. İnternet: # .NET Programları Nasıl Derlenir ve Çalıştırılır? MSIL ve JIT Nedir?
https://youtu.be/MNywsguVPsc
3. İnternet: .NET Compiler Platform ( " Roslyn " ) genişletilebilirliği - Visual Studio | Microsoft Docs
https://docs.microsoft.com/tr-tr/visualstudio/extensibility/dotnet-compiler-platform-roslyn-extensibility?view=vs-2019
4. İnternet: C# Extension Method Nedir ?.
https://medium.com/@serkan22789/c-extension-method-nedir-16dde50f9630
5. İnternet: Alternatives To MVC | ircmaxell's Blog
https://blog.ircmaxell.com/2014/11/alternatives-to-mvc.html
6. İnternet: Architectural pattern - Wikipedia
https://en.wikipedia.org/wiki/Architectural_pattern
7. İnternet: ViewBag, ViewData ve TempData ASP.NET MVC 3 Kullanımı ve Farkları
http://www.aspmvcnet.com/tr/m/razor/viewbag-viewdata-ve-tempdata-asp-net-mvc-3-kullanimi-ve-farklari.html
