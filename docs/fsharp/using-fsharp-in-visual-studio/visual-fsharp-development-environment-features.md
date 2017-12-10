---
title: "F# Geliştirme Ortamı Özellikleri"
description: "Hangi Visual Studio 2012 F #'de desteklenen özellikler hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 809e9a34-b271-4c87-8356-2426b44f4721
ms.openlocfilehash: 05727bf11eccfd64f823dd280b1a19210815ca5a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="visual-f-development-environment-features"></a>Visual F # geliştirme ortamı özellikleri

> [!NOTE]
Bu makale, en son Visual Studio ile güncel değil.  Güncelleştirilecek.

Bu konu hakkında Visual Studio 2012 F #'de desteklenen özellikler bilgiler içerir.

## <a name="project-features"></a>Proje Özellikleri
F # projelerine kullanılabilir şablonları aşağıdaki tabloda özetlenmiştir. Proje ve öğe şablonları hakkında daha fazla bilgi için bkz: [NIB oluşturma projeleri şablonlardan](https://msdn.microsoft.com/library/7c36d86a-6b79-4480-8228-0f925f1204b2).

|Şablon türü|Açıklama|Desteklenen şablonları|
|-------------|-----------|-------------------|
|Proje şablonları|Kullanılabilir proje türleri **yeni proje** iletişim kutusu.|<ul><li>F # uygulaması<br /></li><li>F # kitaplığı<br /></li><li>F # Öğreticisi<br /></li><li>Taşınabilir F # kitaplığı<br /></li><ul/>|
|Öğe şablonları|Dosya türleri kullanılabilir **Yeni Öğe Ekle** iletişim kutusu.|<ul><li>F # kaynak dosyası (.fs)<br /></li><li>F # betiği (.fsx)<br /></li><li>F # imza dosyası (.fsi)<br /></li><li>Yapılandırma dosyası (.config)<br /></li><li>SQL veritabanı bağlantısı (LINQ-SQL türü sağlayıcısı)<br /></li><li>SQL veritabanı bağlantısı (LINQ to Entities türü sağlayıcısı)<br /></li><li>OData hizmeti bağlantısı (LINQ türü sağlayıcısı)<br /></li><li>WSDL hizmeti bağlantısı (tür sağlayıcısı)<br /></li><li>XML dosyası (.xml)<br /></li><li>Metin dosyası<br /></li><ul/>|
Tek başına yürütülebilir çalıştırabilirsiniz bir uygulama oluşturmak için F # uygulaması proje türü seçin. Bir kitaplığı oluşturmak için (diğer bir deyişle, yönetilen bir derleme veya. DLL dosyası) Windows masaüstü platformu üzerinde kullanım için F # kitaplığı seçin. Desteklenen her platformda kullanılabilir taşınabilir bir kitaplığı oluşturmak için F # taşınabilir kitaplığı seçin. F # taşınabilir kitaplık projeleri, Windows mağazası uygulamaları, .NET Framework 4.5 ve Xamarin.iOS Xamarin.Android gibi platformlarında çalışan uygulamalar ile kullanılan F # kitaplığı oluşturmak uygun olan FSharp.Core.dll sürümü başvuru.

Veri erişimi için öğe şablonları hakkında daha fazla bilgi için bkz: [tür sağlayıcıları](../tutorials/type-providers/index.md).

F #'de desteklenen ve desteklenmeyen proje özellikleri özellikler aşağıdaki tabloda özetlenmiştir. Daha fazla bilgi için bkz: [yapılandırma projeleri](configuring-projects.md) ve [Proje Tasarımcısı giriş](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7).

|Proje ayarı|F #'de destekleniyor mu?|Notlar|
|---------------|----------------|-----|
|Kaynak dosyaları|Evet||
|Yapı, hata ayıklama ve başvuru ayarları|Evet||
|Çoklu Sürüm Desteği|Evet||
|Simge ve bildirim|Hayır|Derleyici komut satırı seçenekleri kullanılabilir.|
|ASP.NET İstemci Hizmetleri|Hayır||
|ClickOnce|Hayır|Bir istemci projesi başka bir .NET Framework dilde varsa kullanın.|
|Tanımlayıcı ad oluşturma|Hayır|Derleyici komut satırı seçenekleri kullanılabilir.|
|Yayımlama derleme ve sürüm oluşturma|Hayır||
|Kod çözümleme|Hayır|Kod çözümleme araçları el ile veya yapı sonrası komut parçası olarak çalıştırabilirsiniz.|
|Güvenlik (güven düzeylerini değiştirme)|Hayır||

## <a name="code-and-text-editor-features"></a>Kod ve metin düzenleyici özellikleri
F #'de Visual Studiocode ve metin düzenleyicileri, aşağıdaki özellikleri desteklenir. Visual Studio ve metin düzenleyici özelliklerini kod düzenleme hakkında genel bilgi için bkz: [kod ve Metin Düzenleyici'de kod yazma](/visualstudio/ide/writing-code-in-the-code-and-text-editor).

|Özellik|Açıklama|F #'de destekleniyor mu?|
|-------|-----------|----------------|
|Otomatik olarak açıklama|Yorum yapmak veya kodun bölümlerine sağlar.|Evet|
|Otomatik biçimlendirme|Kodu standart girintileme ve stil ile yeniden biçimlendirir.|Hayır|
|Yer işaretleri|Düzenleyicide yerler kaydetmenizi sağlar.|Evet|
|Girinti değiştirme|Girintileri veya seçili satırları girintileri geri alır.|Evet|
|[Metin Bulma ve Değiştirme](/visualstudio/ide/finding-and-replacing-text)|Dosya, proje veya çözüm arayın ve potansiyel olarak metin değiştirmenizi sağlar.|Evet|
|.NET Framework API tanımı gidin|İmleç bir .NET Framework API üzerinde konumlandırıldığında .NET Framework meta verilerinden oluşturulan kodu gösterir.|Hayır|
|Kullanıcı tanımlı API için Tanıma Git|İmleç imleci kodunuzda varlık tanımlandığı konuma taşır, tanımlı bir program varlığı üzerinde olduğunda.|Evet|
|Satıra Gitme|Satır numarası ile bir dosyada belirli bir satıra Git olanak tanır.|Evet|
|Dosyanın üst kısmındaki gezinti çubukları|Kodda, konumları, örneğin, işlev adı atlamak etkinleştirir.|Evet|
|Anahat oluşturma. Bkz: [anahat oluşturma](/visualstudio/ide/outlining).|Daha kısa bir görünüm oluşturmak için kodun bölümlerini daraltma olanak tanır.|Evet|
|Sekmelere ayırma|Boşluk, sekme dönüştürür.|Evet|
|Tür renklendirme|Özel bir renk ile tanımlanmış tür adları gösterir.|Evet|
|Hızlı bulun. Hızlı bulma, bulma ve değiştirme penceresi bakın.|Bir dosya veya proje aramanıza olanak tanır.|Evet|

## <a name="intellisense-features"></a>IntelliSense özellikleri
F #'de desteklenen ve desteklenmeyen IntelliSense özellikler aşağıdaki tabloda özetlenmiştir. IntelliSense hakkında genel bilgi için bkz: [kullanarak IntelliSense](/visualstudio/ide/using-intellisense).

|Özellik|Açıklama|F #'de destekleniyor mu?|
|-------|-----------|----------------|
|Otomatik olarak uygulanan arabirimler|Arabirim yöntemleri için kod saplamalar oluşturur.|Hayır|
|Kod parçacıkları|Kod ortak kodlama yapıları kitaplığından konulara yerleştirir.|Hayır|
|Tam Sözcük|Siz yazarken kelimeleri ve isimleri tamamlayarak yazmadan kazandırır.|Evet|
|İlk tamamlanma modu|Etkinleştirildiğinde, word tamamlamanın, birini seçin veya beklemek yerine, yazarken ilk eşleşmeyi seçmesini sağlar **CTRL + Ara çubuğu**.|Hayır|
|Kod öğeleri oluşturma|Çeşitli yapılar için saplama kodu oluşturmanızı sağlar.|Hayır|
|Üyeleri Listeleme|Üye erişimi işleci (.) yazın, bir tür için Üyeler gösterilir.|Evet|
|Kullanımları/Open düzenleme|Ad alanları tarafından başvurulan düzenler **kullanarak** deyimleri C# veya **açın** F # yönergeleri.|Hayır|
|Parametre Bilgisi|Bir işlev çağrısı yazarken parametreler hakkında yararlı bilgiler gösterir.|Evet|
|Hızlı Bilgi|Herhangi bir tanımlayıcı için bütün bildirimi kodunuzda görüntüler.|Evet|
F # kodunu yeniden düzenleme, Visual Studio 2012'de desteklenmez.

## <a name="debugging-features"></a>Hata ayıklama özelliği
Aşağıdaki tabloda, F # kodda hata ayıklarken kullanılabilen özellikler özetlenmiştir. Visual Studio hata ayıklayıcısı hakkında genel bilgi için bkz: [Visual Studio'da hata ayıklamayı](https://msdn.microsoft.com/library/sc65sadd.aspx).

|Özellik|Açıklama|F #'de destekleniyor mu?|
|-------|-----------|----------------|
|Otomatik değişkenler penceresi|Otomatik veya geçici değişkenleri gösterir.|Hayır|
|Kesme noktaları|Hata ayıklama sırasında kodu yürütme belirli zamanlarda duraklatmanıza da olanak sağlar.|Evet|
|Koşullu kesme noktaları|Yürütme duraklaması gerekip gerekmediğini belirler bir koşulu test kesme noktaları sağlar.|Evet|
|Düzenle ve Devam Et|Değiştirilebilir ve çalışan bir program hata ayıklayıcı durdurup olmadan'hata ayıklama gibi derlenmiş kod sağlar.|Hayır|
|İfade değerlendirici|Değerlendirir ve çalışma zamanında kodu yürütür.|Hayır, ama C# ifade değerlendiricisi kullanılabilir, ancak C# sözdizimi kullanmanız gerekir.|
|Geçmiş hata ayıklama|Daha önce yürütülen koda adım olanak tanır.|Evet|
|Yerel öğeler penceresi|Değerleri ve değişkenleri tanımlanmış yerel olarak gösterir.|Evet|
|İmleci çalıştırın|İmlecin bulunduğu satırı ulaşılana kadar kod yürütmesine olanak tanır.|Evet|
|Girme|Yürütme ilerleyin ve herhangi bir işlev çağrısına taşıma sağlar.|Evet|
|Adımlama|Geçerli yığın çerçevesini yürütme ilerleyin ve herhangi bir işlev çağrısına taşıma sağlar.|Evet|

## <a name="additional-tools"></a>Ek araçlar
F # için destek Visual Studio Araçları'nda aşağıdaki tabloda özetlenmiştir.

|Aracı|Açıklama|F #'de destekleniyor mu?|
|----|-----------|----------------|
|Çağrı Hiyerarşisi|Görüntüler, kodunuzda iç içe geçmiş yapısını işlevi çağırır.|Hayır|
|Kod ölçümleri|Satır sayısı gibi kodu hakkında bilgi toplar.|Hayır|
|Sınıf Görünümü|Bir proje kodda tür tabanlı bir görünümünü sağlar.|Hayır|
|[Hata Listesi Penceresi](/visualstudio/ide/reference/error-list-window)|Hataların listesini kodu gösterir.|Evet|
|[F # Etkileşimli](../tutorials/fsharp-interactive/index.md)|Yazın (veya kopyalayıp yapıştırmak için) F # kod ve projenizin yapı bağımsız olarak hemen çalıştırmak sağlar. F # Etkileşimli penceredir oku, değerlendir, yazdırma döngü (Çoğaltma).|Evet|
|Nesne Tarayıcısı|Bir derlemede türleri görüntülemenize olanak tanır.|Derlenmiş derlemelerde göründükleri gibi tam olarak yazar olarak F # türleri görünmez. F # türleri derlenmiş gösterimi göz atabilirsiniz ancak F # göründükleri gibi türleri görüntüleyemezsiniz.|
|[Çıktı Penceresi](/visualstudio/ide/reference/output-window)|Oluşum çıktısını görüntüler.|Evet|
|Performans Analizi|Kodunuzu performansını ölçmek için araçlar sağlar.|Evet|
|Özellikler Penceresi|Görüntüler ve odaklanmış geliştirme ortamında nesnenin özelliklerini düzenlemeyi sağlar.|Evet|
|[Sunucu Gezgini](https://msdn.microsoft.com/library/x603htbk.aspx)|Çeşitli sunucu kaynakları ile etkileşim kurmak için yöntemler sağlar.|Evet|
|Çözüm Gezgini|Projeler ve dosyaları görüntülemek ve yönetmek etkinleştirir.|Evet|
|Görev Listesi|Kodunuza iş öğelerini yönetmenize olanak sağlar.|Evet|
|Test projeleri|Yardımcı özellikleri kodunuzu test sağlar.|Hayır|
|Araç Kutusu|Denetimleri ve metin veya kod bölümlerini gibi sürüklenebilir nesneleri içeren sekmeleri görüntüler.|Evet|

## <a name="see-also"></a>Ayrıca Bkz.
 [F # Visual Studio ile çalışmaya başlama](../get-started/get-started-visual-studio.md)  
 [Projeleri yapılandırma](configuring-projects.md)  
