---
title: Winres.exe (Windows, kaynak, yerelleştirme, Düzenleyici)
ms.date: 08/15/2018
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- Windows Resource Localization Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c9a14c2ea2d7d817aacca1fa25b04ac643f16bf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296660"
---
# <a name="winresexe-windows-resource-localization-editor"></a>Winres.exe (Windows, kaynak, yerelleştirme, Düzenleyici)

Windows Kaynak yerelleştirme Düzenleyicisi Winres.exe, yerelleştirme uzmanlarının formlar tarafından kullanılan Windows Forms kullanıcı arabirimi (UI) kaynaklarını yerelleştirmesine yardımcı olan bir görsel düzen aracıdır. Winres.exe için girdi olarak kullanılan .resx veya .resources dosyaları Microsoft Visual Studio gibi bir görsel tasarım ortamı kullanarak oluşturulabilir. .NET Framework uygulamalarında kaynakları dağıtma hakkında daha fazla bilgi için bkz. [masaüstü uygulamalarında kaynakların](../../../docs/framework/resources/index.md).

Winres.exe, Visual Studio ile yüklenir. Aracı çalıştırmak için Visual Studio için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

## <a name="syntax"></a>Sözdizimi

```
winres resourceFile
winres /?
```

## <a name="arguments"></a>Arguments

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`resourceFile`|Yerelleştirilecek kaynak dosyası. Bu dosya, Visual Studio tasarımcısı tarafından oluşturulan Windows Forms formu .resx veya .resources dosyası olmalıdır. Winres.exe genel .resx veya .resources dosyalarını açamaz.|

|Seçenek|Açıklama|
|------------|-----------------|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

## <a name="remarks"></a>Açıklamalar

Bir Windows Forms projesindeki formda bulunan arabirim öğelerinin durumu genellikle kaynak dosyalarında depolanır; bunlar .resx uzantılı XML tabanlı dosyalar veya karşılık gelen derlenmiş, .resources uzantılı ikili sürümlerdir. Winres.exe, her iki dosya türünün Visual Studio tasarım ortamı dışında sınırlı şekilde düzenlenmesine olanak veren bir araçtır. Özellikle aşağıdaki türden düzenleme işlemlerine izin verir:

- Bir nötr veya belirli kültür kaynak dosyası, formun arabirim özelliklerini veya denetimlerini (metin, boyut veya konum gibi) değiştirecek şekilde düzenlenebilir.

- Nötr veya belirli kültür kaynak dosyaları varsayılan kaynak dosyasından oluşturulabilir.

- Bir kültür kaynak dosyası başka bir kültür kaynak dosyası olarak kaydedilebilir. Örneğin, İngilizce (ABD) kaynak dosyası Lehçe kaynak dosyası olarak kaydedilebilir. Genellikle yeni dosya daha sonra yeni kültür ile uyumlu olacak şekilde düzenlenir.

Ayrıca bkz: [kaynakların hiyerarşik organizasyonu yerelleştirme için](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/756hydy4(v=vs.110)) veya [kaynakların hiyerarşik organizasyonu yerelleştirme için](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/756hydy4(v=vs.120)).

Winres.exe, bir .resx dosyasını karşılık gelen .resources dosyasına dönüştüremez; bunun yerine Resgen.exe aracını kullanmalısınız. Resgen.exe hakkında daha fazla bilgi için bkz: [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

Winres.exe, kaynak koduna erişmeden bir Windows Forms formunun tasarım zamanı sürümünü yalnızca kaynak dosyasından yeniden oluşturan grafiksel bir uygulamadır. Winres.exe, Visual Studio'nun barındıran **Windows Forms Form Tasarımcısı** ve **özellikleri** penceresi. Bu özellikler, Windows Forms formu içeren bir .resources veya .resx dosyasının görsel olarak düzenlenmesine olanak verir. Winres.exe yerelleştiriciler genellikle Denetim etiketlerini düzenlemek ve hedef kültürle etiketlerini içerecek şekilde denetimleri boyutunu ve konumunu ayarlamak için kullanır.

Winres.exe bir denetimin türünü çözümleyemezse, yerelleştirilmiş .resx veya .resources dosyasında bir yer tutucu denetimi oluşturur. Yer tutucu denetimi Windows Forms formunda taranmış bir pencere olarak görüntülenir. Taranmış pencerenin boyutu ve konumu gerçek denetiminkilerle aynıdır. Tüm kullanılabilir, yerelleştirilebilir özellikleri yer tutucu denetiminin görünür **özellikleri** penceresi. Yer tutucu denetiminde yaptığınız tüm değişiklikler asıl denetim için kaydedilir.

## <a name="winresexe-versus-visual-studio"></a>Winres.exe ve Visual Studio

Genel olarak, bir uygulamanın Windows Forms formlarını yerelleştirmeye başlamadan önce, yerelleştirme aracı olarak Visual Studio'yu mu yoksa Winres.exe'yi mi kullanmak istediğinize karar vermelisiniz. Sürüm uyumluluğu, daha sonra açıklandığı gibi, bir araçtan diğerine geçiş yapmasını engelleyebilir.

Visual Studio'nun avantajı, bir uygulamayı hem geliştirmek hem de yerelleştirmek için kullanabilmenizdedir. Geliştirme işlemi tamamlandıktan sonra bir formu yerelleştirmek için formun ayarlayın <xref:System.ComponentModel.LocalizableAttribute> ( **yerelleştirilebilir** özelliğinde **özellikleri** Düzenleyici) için `true` değiştirip kendi  **Dil** özelliğini de istediğiniz hedef kültüre. Daha sonra, dizeleri düzenleyin ve denetimlerin konumu ile boyutunu hedef kültürün dizelerine uygun olacak şekilde ayarlayın. Yerelleştirilmiş .resx dosyasını kaydettiğinizde, Visual Studio dosyaya yalnızca yerelleştirilebilir özellikleri (hedef kültürde değiştirilen özellikler) yazar. Visual Studio, yerelleştirilmiş .resx dosyası için bir uydu derlemesini doğru dizin konumunda otomatik olarak oluşturur.

Visual Studio tümleşik bir geliştirme ve yerelleştirme ortamı sağlasa da, Winres.exe, yerelleştirme üçüncü taraf yerelleştiriciler tarafından yapılacaksa yapıldığında kullanılacak önerilen araç winres.exe'dir. Winres.exe yalnızca bir yerelleştirme aracı olduğu için, bir uygulamanın kodu ile yerelleştirilecek formlar arasında daha net bir ayrım sağlar, ki bu da büyük projeleri yönetirken daha büyük bir kolaylık demektir.

## <a name="using-winresexe"></a>Winres.exe'yi kullanma

Winres.exe kullanarak yerelleştirmek için önce bir görsel tasarımcı benzer kullanarak bir uygulama geliştirmeniz gerekir **Windows Form Tasarımcısı** Visual Studio'da. Geliştirme tamamlandığında, formun ayarlamak <xref:System.ComponentModel.LocalizableAttribute> ( **yerelleştirilebilir** özelliğinde **özellikleri** Düzenleyici) için `true`ve sonra kapatmak için varsayılan kültürün .resx dosyasını el bir üçüncü taraf yerelleştiriciye. Bu .resx dosyası özgün formun tasarım zamanı sürümünü yeniden oluşturmak için Winres.exe'nin kullandığı ek bilgileri içerir.

> [!NOTE]
> Winres.exe varsayılan kaynak dosyayı düzenlemek için kullanılamaz. Winres.exe, değişen tüm özellikleri yerelleştirilmiş özellikler olarak yorumlar ve bunları hedef kültür kaynak dosyasına kaydeder.

Kültür kaynak dosyalarının son sürümleri son olarak uygulamanın yerelleştirilmiş sürümlerini oluşturmak için kullanılabilir. Daha fazla bilgi için [masaüstü uygulamalarında kaynakların](../../../docs/framework/resources/index.md).

Winres.exe, aşağıdaki özellikler ve yetenekler vardır:

- Winres Tek Dosya Modu'nda (SFM) veya Visual Studio Dosya Modu'nda (VSFM) çalışabilir. SFM, form ve içeriği hakkındaki tüm bilgilerin kaynak dosyada depolandığı eski moddur. VSFM kültürel değişiklikleri yalnızca kaynak dosyasında depolar.

- Bir hata bildirimi penceresi ana pencerenin sol için yerleştirilmiş.

- Kısayol tuşlarını çoğaltmaları kontrol: gelen **biçimi** menüsünde tıklatın **kısayol tuşlarını denetle** komutu.

## <a name="version-compatibility"></a>Sürüm Uyumluluğu

Kullanmakta olduğunuz .NET Framework ile yayımlanan Winres.exe sürümünü kullanmanız gerekir. Aşağıdaki tabloda uyumlu sürümler listelenmiştir:

|Visual Studio|.NET Framework|Winres.exe|
|-------------------|--------------------|----------------|
|Visual Studio .NET 2002|1.0|1.0|
|Visual Studio .NET 2003|1.1|1.1|
|Visual Studio 2005|2,0|2,0|
|Visual Studio 2008|3.0 ve 3.5|3.0 ve 3.5|
|Visual Studio 2010|4.0|4.0|
|Visual Studio 2017|4.6|4.6|

> [!NOTE]
> VSFM'de, Visual Studio ile uyumluluk avantajı bulunuyor olsa da, kaynak dosyaya yalnızca değiştirilmiş değerleri depoladığından, Winres.exe geçerli kaynak dosyanın üst öğelerinin aynı dizinde bulunmasını gerektirir. Örneğin, düzenleme `TestApp.de-DE.resources`, Almanya kaynak dosyasında Almanca varsayılan kaynak dosyası gerektirir `TestApp.resx`ve büyük olasılıkla kültür kaynak dosyası `TestApp.de.resources`.

## <a name="examples"></a>Örnekler

### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Bir formla ilişkili .resx veya .resources dosyasını yerelleştirmek için

1. Tür `winres` Winres.exe'yi çalıştırmak üzere Geliştirici komut istemi.

2. Yerelleştirilecek bir form için varsayılan kaynakları açmak için **açın** komutunu **dosya** menüsünü açmak için dosyaya gidin.

     -veya-

     Winres.exe'yi başlattığınızda komut satırında açılacak dosyayı belirtin.

     Aşağıdaki komut Winres.exe'yi başlatır ve ilişkili formu yükler `TestApp.resx` Form Tasarımcısı'nda.

    ```
    winres TestApp.resx
    ```

     Aşağıdaki komut Winres.exe'yi başlatır ve ilişkili formu yükler `TestApp.resources` Form Tasarımcısı'nda.

    ```
    winres TestApp.resources
    ```

    > [!NOTE]
    > Kaynaklarını düzenlediğiniz form devralınmış bir form ise, hem formun içindeki derleme hem de devralan (türetilmiş) formu içeren derleme Genel Derleme Önbelleği'ne (GAC) kaydettirilmeli veya WinRes.exe ile aynı dizinde bulunmalıdır. .NET Framework bileşenlerini GAC'a yükleme hakkında daha fazla bilgi için bkz. [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md).

3. Form üzerinde denetimleri seçin ve değiştirmek, <xref:System.Windows.Forms.Control.Text%2A> ve yerelleştirilmiş kültür ve dilini yansıtacak şekilde diğer özellikleri. Yerelleştirilmiş metnin sığmasını sağlayacak şekilde denetimleri gerektiği gibi taşıyın veya yeniden boyutlandırın.

4. .Resx veya .resources dosyasının yerelleştirilmiş sürümünü kaydetmek için tıklatın **Kaydet** simgesini veya aynı komutu **dosya** menüsü. Araç görüntüler **kültür Seç** penceresi.

5. Uygun kültürü ve dosya modunu seçin, ardından tıklayın **Tamam**.

   Aracı'nı yerelleştirilmiş kaynak dosyaları için çalışma zamanındaki beklediği adlandırma kuralını kullanarak dosyayı kaydeder. Örneğin, yerelleştiriyorsanız `TestApp.resources` Almanya'da Almanca için araç dosyası olarak kaydeder. `TestApp.de-DE.resources`. Yerelleştiriyorsanız `TestApp.resx` Almanya'da Almanca için araç dosyası olarak kaydeder. `TestApp.de-DE.resx`. Kaynak adlandırma kuralları hakkında daha fazla bilgi için bkz: [kaynakları paketleme ve dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Çalışma zamanı tarafından kullanılan önceden tanımlanmış kültür adlarının listesi için bkz. <xref:System.Globalization.CultureInfo> sınıfı.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.LocalizableAttribute>
- <xref:System.Globalization.CultureInfo>
- <xref:System.Resources.ResourceManager>
- <xref:System.Resources.ResourceReader>
- <xref:System.Resources.ResourceWriter>
- [Araçlar](../../../docs/framework/tools/index.md)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
