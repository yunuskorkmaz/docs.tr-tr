---
title: Winres.exe (Windows Forms Kaynak Düzenleyici)
ms.date: 03/30/2017
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69ba816e5b7cf05ef094153b7ff044d573ac1760
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472587"
---
# <a name="winresexe-windows-forms-resource-editor"></a>Winres.exe (Windows Forms Kaynak Düzenleyici)
Windows Formları Kaynak Düzenleyicisi Winres.exe, yerelleştirme uzmanlarının formlar tarafından kullanılan Windows Formları kullanıcı arabirimi (UI) kaynaklarını yerelleştirmesine yardımcı olan görsel bir düzen aracıdır. Winres.exe için girdi olarak kullanılan .resx veya .resources dosyaları Microsoft Visual Studio gibi bir görsel tasarım ortamı kullanarak oluşturulabilir. .NET Framework uygulamalarında kaynakları dağıtma hakkında daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakları](../../../docs/framework/resources/index.md).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
winres resourceFile   
winres /?   
```  
  
## <a name="remarks"></a>Açıklamalar  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|`resourceFile`|Yerelleştirilecek kaynak dosyası. Bu dosya, Visual Studio tasarımcısı tarafından oluşturulan Windows Forms formu .resx veya .resources dosyası olmalıdır. Winres.exe genel .resx veya .resources dosyalarını açamaz.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
 Bir Windows Forms projesindeki formda bulunan arabirim öğelerinin durumu genellikle kaynak dosyalarında depolanır; bunlar .resx uzantılı XML tabanlı dosyalar veya karşılık gelen derlenmiş, .resources uzantılı ikili sürümlerdir. Winres.exe, her iki dosya türünün Visual Studio tasarım ortamı dışında sınırlı şekilde düzenlenmesine olanak veren bir araçtır. Özellikle aşağıdaki türden düzenleme işlemlerine izin verir:  
  
-   Bir nötr veya belirli kültür kaynak dosyası, formun arabirim özelliklerini veya denetimlerini (metin, boyut veya konum gibi) değiştirecek şekilde düzenlenebilir.  
  
-   Nötr veya belirli kültür kaynak dosyaları varsayılan kaynak dosyasından oluşturulabilir.  
  
-   Bir kültür kaynak dosyası başka bir kültür kaynak dosyası olarak kaydedilebilir. Örneğin, İngilizce (ABD) kaynak dosyası Lehçe kaynak dosyası olarak kaydedilebilir. Genellikle yeni dosya daha sonra yeni kültür ile uyumlu olacak şekilde düzenlenir.  
  
 Ayrıca bkz. [yerelleştirme, hiyerarşik kuruluş kaynakları](http://msdn.microsoft.com/library/756hydy4\(v=vs.110\)) veya [yerelleştirme, hiyerarşik kuruluş kaynakları](http://msdn.microsoft.com/library/756hydy4\(v=vs.120\)).  
  
 Winres.exe, bir .resx dosyasını karşılık gelen .resources dosyasına dönüştüremez; bunun yerine Resgen.exe aracını kullanmalısınız. Resgen.exe hakkında daha fazla bilgi için bkz: [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  
  
 Winres.exe, kaynak koduna erişmeden bir Windows Forms formunun tasarım zamanı sürümünü yalnızca kaynak dosyasından yeniden oluşturan grafiksel bir uygulamadır. Winres.exe, Visual Studio'nun Windows Forms Form Tasarımcısı ve Özellikler penceresini barındırır. Bu özellikler, Windows Forms formu içeren bir .resources veya .resx dosyasının görsel olarak düzenlenmesine olanak verir. Yerelleştiriciler genellikle hedef kültüre uygun olacak şekilde denetim etiketlerini düzenlemek ve denetimlerin konumu ile boyutunu ayarlamak için Winres.exe'yi kullanırlar.  
  
 Winres.exe bir denetimin türünü çözümleyemezse, yerelleştirilmiş .resx veya .resources dosyasında bir yer tutucu denetimi oluşturur. Yer tutucu denetimi Windows Forms formunda taranmış bir pencere olarak görüntülenir. Taranmış pencerenin boyutu ve konumu gerçek denetiminkilerle aynıdır. Yer tutucu denetiminin tüm kullanılabilir, yerelleştirilebilir özellikleri Özellikler penceresinde görünür. Yer tutucu denetiminde yaptığınız tüm değişiklikler asıl denetim için kaydedilir.  
  
## <a name="winresexe-versus-visual-studio"></a>Winres.exe ve Visual Studio  
 Genel olarak, bir uygulamanın Windows Forms formlarını yerelleştirmeye başlamadan önce, yerelleştirme aracı olarak Visual Studio'yu mu yoksa Winres.exe'yi mi kullanmak istediğinize karar vermelisiniz. Sürüm uyumluluğu, daha sonra açıklandığı gibi, bir araçtan diğerine geçiş yapmasını engelleyebilir.  
  
 Visual Studio'nun avantajı, bir uygulamayı hem geliştirmek hem de yerelleştirmek için kullanabilmenizdedir. Formun geliştirme tamamlandıktan sonra bir form yerelleştirme ayarlayın <xref:System.ComponentModel.LocalizableAttribute> ( **yerelleştirilebilir** özellikleri Düzenleyicisi'nde özelliği) için `true` değiştirip kendi **dil** özelliği İstenen hedef kültür. Daha sonra, dizeleri düzenleyin ve denetimlerin konumu ile boyutunu hedef kültürün dizelerine uygun olacak şekilde ayarlayın. Yerelleştirilmiş .resx dosyasını kaydettiğinizde, Visual Studio dosyaya yalnızca yerelleştirilebilir özellikleri (hedef kültürde değiştirilen özellikler) yazar. Visual Studio, yerelleştirilmiş .resx dosyası için bir uydu derlemesini doğru dizin konumunda otomatik olarak oluşturur.  Ayrıca bkz. [izlenecek yol: Windows Formları yerelleştirme](http://msdn.microsoft.com/library/y99d1cd3\(v=vs.110\)).  
  
 Visual Studio tümleşik bir geliştirme ve yerelleştirme ortamı sağlasa da, yerelleştirme üçüncü taraf yerelleştiriciler tarafından yapılacaksa önerilen araç Winres.exe'dir. Winres.exe yalnızca bir yerelleştirme aracı olduğu için, bir uygulamanın kodu ile yerelleştirilecek formlar arasında daha net bir ayrım sağlar, ki bu da büyük projeleri yönetirken daha büyük bir kolaylık demektir.  
  
## <a name="using-winresexe"></a>Winres.exe'yi kullanma  
 Winres.exe kullanarak yerelleştirmek için, önce Visual Studio'da Forms Tasarımcısı gibi görsel bir tasarımcıyı kullanarak bir uygulama geliştirmeniz gerekir. Geliştirme tamamlandığında, formun ayarlamak <xref:System.ComponentModel.LocalizableAttribute> ( **yerelleştirilebilir** özelliği özellikleri Düzenleyicisi'nde) için `true`ve ardından varsayılan kültür için .resx dosyası kapalı bir üçüncü taraf yerelleştiriciye el. Bu .resx dosyası özgün formun tasarım zamanı sürümünü yeniden oluşturmak için Winres.exe'nin kullandığı ek bilgileri içerir.  
  
> [!CAUTION]
>  Winres.exe varsayılan kaynak dosyayı düzenlemek için kullanılamaz. Winres.exe, değişen tüm özellikleri yerelleştirilmiş özellikler olarak yorumlar ve bunları hedef kültür kaynak dosyasına kaydeder.  
  
 Kültür kaynak dosyalarının son sürümleri son olarak uygulamanın yerelleştirilmiş sürümlerini oluşturmak için kullanılabilir. Daha fazla bilgi için bkz: [masaüstü uygulamalarında kaynakları](../../../docs/framework/resources/index.md).  
  
 Winres.exe 2.0 sürümünde aşağıdaki özellikler ve yetenekler vardır:  
  
-   Winres Tek Dosya Modu'nda (SFM) veya Visual Studio Dosya Modu'nda (VSFM) çalışabilir. SFM, form ve içeriği hakkındaki tüm bilgilerin kaynak dosyada depolandığı eski moddur. VSFM kültürel değişiklikleri yalnızca kaynak dosyasında depolar.  
  
-   Arabirime ana pencerenin sol alt tarafında bir hata bildirimi penceresi eklenmiştir.  
  
-   Kısayol tuşları çoğaltmaları kontrol: biçimi menüden **kısayollarıyla denetleyin** komutu.  
  
## <a name="version-compatibility"></a>Sürüm Uyumluluğu  
 Kaynak dosyaların biçimi Visual Studio .NET 2002 ve Visual Studio 2005 sürümleri arasında değiştiğinden, Winres.exe de uyumlu olacak şekilde değiştirilmiştir. Bu nedenle genel kural olarak, uygulamayı oluşturmak için kullanmakta olduğunuz .NET Framework ile birlikte yayımlanan Winres.exe sürümünü kullanmanız gerekir. Aşağıdaki tabloda uyumlu sürümler listelenmiştir.  
  
|Visual Studio|.NET Framework|Winres.exe|  
|-------------------|--------------------|----------------|  
|Visual Studio .NET 2002|1.0|1.0|  
|Visual Studio .NET 2003|1.1|1.1|  
|Visual Studio 2005|2,0|2,0|  
|Visual Studio 2008|3.0 ve 3.5|3.0 ve 3.5|  
|Visual Studio 2010|4.0|4.0|  
  
 Winres.exe 2.0 sürümü ile daha eski bir kaynak dosyasını açmaya çalışırsanız, dosyasının biçimini .NET Framework 2.0 sürümü ile uyumlu olacak şekilde yükseltmeniz istenir.  
  
 .NET Framework'ün 2.0'dan önceki sürümlerinde, Winres.exe ve Visual Studio Form Tasarımcısı kültüre özgü olan ve olmayan uyumsuz kaynak dosyaları oluşturmaktaydı. Bu nedenle, yerelleştirme işlemi başladıktan sonra yalnızca aynı aracı kullanarak devam etmek zorundaydınız. Ancak, Winres.exe 2.0 sürümüyle birlikte, Visual Studio Dosya Modu (VSFM) eklendi. Adından da anlaşılacağı gibi, bu uyumluluk modunda kaydedilmiş bir kaynak dosyası her iki araçla da düzenlenebilmektedir.  
  
> [!NOTE]
>  VSFM'de, Visual Studio ile uyumluluk avantajı bulunuyor olsa da, kaynak dosyaya yalnızca değiştirilmiş değerleri depoladığından, Winres.exe geçerli kaynak dosyanın üst öğelerinin aynı dizinde bulunmasını gerektirir. Örneğin, düzenleme `TestApp.de-DE.resources`, Almanca Almanya kaynak dosyasında gerektirir varsayılan kaynak dosyasının varlığı, `TestApp.resx`ve büyük olasılıkla kültür Tarafsız kaynak dosyası `TestApp.de.resources`.  
  
## <a name="examples"></a>Örnekler  
  
#### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Bir formla ilişkili .resx veya .resources dosyasını yerelleştirmek için  
  
1.  Tür `winres` Winres.exe çalıştırmak için geliştirici komut istemindeki.  
  
2.  Yerelleştirme için bir form için varsayılan kaynaklar'ı açmak için **açmak** komutunu **dosya** menü ve açmak için dosyaya gidin.  
  
     -veya-  
  
     Winres.exe'yi başlattığınızda komut satırında açılacak dosyayı belirtin.  
  
     Aşağıdaki komut Winres.exe başlar ve ilişkili form yüklediğinde `TestApp.resx` Form tasarımcısında.  
  
    ```  
    winres TestApp.resx  
    ```  
  
     Aşağıdaki komut Winres.exe başlar ve ilişkili form yüklediğinde `TestApp.resources` Form tasarımcısında.  
  
    ```  
    winres TestApp.resources  
    ```  
  
    > [!NOTE]
    >  Kaynaklarını düzenlediğiniz form devralınmış bir form ise, hem formun içindeki derleme hem de devralan (türetilmiş) formu içeren derleme Genel Derleme Önbelleği'ne (GAC) kaydettirilmeli veya WinRes.exe ile aynı dizinde bulunmalıdır. GAC içine .NET Framework bileşenlerini yükleme hakkında daha fazla bilgi için bkz: [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md).  
  
3.  Form üzerinde denetimleri seçin ve değiştirin kendi <xref:System.Windows.Forms.Control.Text%2A> ve diğer özellikleri yerelleştirilmiş kültür ve dili yansıtır. Yerelleştirilmiş metnin sığmasını sağlayacak şekilde denetimleri gerektiği gibi taşıyın veya yeniden boyutlandırın.  
  
4.  .Resx veya .resources dosyası yerelleştirilmiş sürümünü kaydetmek için tıklatın **kaydetmek** simgesine veya aynı komutunu **dosya** menüsü. Aracı görüntüler **seçin kültür** penceresi.  
  
5.  Uygun kültür ve dosya modunu seçip'i tıklatın **Tamam**. Araç, çalışma zamanının yerelleştirilmiş kaynak dosyaları için beklediği adlandırma kuralını kullanarak dosyayı kaydeder. Örneğin, yerelleştirme `TestApp.resources` Almanya Almanca için aracı dosyası olarak kaydeder `TestApp.de-DE.resources`. Yerelleştirme, `TestApp.resx` Almanya Almanca için aracı dosyası olarak kaydeder `TestApp.de-DE.resx`. Kaynak adlandırma kuralları hakkında daha fazla bilgi için bkz: [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Çalışma zamanı tarafından kullanılan önceden tanımlanmış kültür adları listesi için bkz: <xref:System.Globalization.CultureInfo> sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.LocalizableAttribute>  
 <xref:System.Globalization.CultureInfo>  
 <xref:System.Resources.ResourceManager>  
 <xref:System.Resources.ResourceReader>  
 <xref:System.Resources.ResourceWriter>  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)  
 [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
