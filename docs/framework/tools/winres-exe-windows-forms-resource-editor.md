---
title: Winres.exe (Windows Kaynak Yerelleştirme Düzenleyicisi)
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
ms.openlocfilehash: 2cfb2d9874b34eef78fe462e0270fd70307a9f61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715703"
---
# <a name="winresexe-windows-resource-localization-editor"></a>Winres.exe (Windows Kaynak Yerelleştirme Düzenleyicisi)

Windows Kaynak Yerelleştirme Düzenleyicisi, Winres.exe, yerelleştirme uzmanlarının formlar tarafından kullanılan Windows Forms kullanıcı arabirimi (UI) kaynaklarını yerelleştirmelerine yardımcı olan bir görsel düzen aracıdır. Winres.exe için girdi olarak kullanılan .resx veya .resources dosyaları Microsoft Visual Studio gibi bir görsel tasarım ortamı kullanarak oluşturulabilir. .NET Framework uygulamalarında kaynak dağıtma hakkında bilgi için [Masaüstü Uygulamalarındaki Kaynaklar'a](../resources/index.md)bakın.

Winres.exe Visual Studio ile yüklenir. Aracı çalıştırmak için Visual Studio için Geliştirici Komut Komut Ustem'ini kullanın. Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

## <a name="syntax"></a>Sözdizimi

```console
winres resourceFile
winres /?
```

## <a name="arguments"></a>Bağımsız Değişkenler

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

Ayrıca bkz. [Yerelleştirme için Kaynakların Hiyerarşik Organizasyonu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/756hydy4(v=vs.110)) veya [Yerelleştirme için Kaynakların Hiyerarşik Organizasyonu.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/756hydy4(v=vs.120))

Winres.exe, bir .resx dosyasını karşılık gelen .resources dosyasına dönüştüremez; bunun yerine Resgen.exe aracını kullanmalısınız. Resgen.exe hakkında daha fazla bilgi için Bkz. [Resgen.exe (Kaynak Dosya Üreteci)](resgen-exe-resource-file-generator.md).

Winres.exe, kaynak koduna erişmeden bir Windows Forms formunun tasarım zamanı sürümünü yalnızca kaynak dosyasından yeniden oluşturan grafiksel bir uygulamadır. Winres.exe, Visual Studio'nun **Windows Forms Form Designer** ve **Properties** pencerelerine ev sahipliği yapmaktadır. Bu özellikler, Windows Forms formu içeren bir .resources veya .resx dosyasının görsel olarak düzenlenmesine olanak verir. Genellikle, yerelleştiriciler kontrol etiketlerini ayarlamak ve denetimlerin konumunu ve boyutunu hedef kültür etiketlerini barındıracak şekilde ayarlamak için Winres.exe kullanır.

Winres.exe bir denetimin türünü çözümleyemezse, yerelleştirilmiş .resx veya .resources dosyasında bir yer tutucu denetimi oluşturur. Yer tutucu denetimi Windows Forms formunda taranmış bir pencere olarak görüntülenir. Taranmış pencerenin boyutu ve konumu gerçek denetiminkilerle aynıdır. Yer tutucu denetimi için kullanılabilir tüm yerelleştirilebilir özellikler **Özellikler** penceresinde görünür. Yer tutucu denetiminde yaptığınız tüm değişiklikler asıl denetim için kaydedilir.

## <a name="winresexe-versus-visual-studio"></a>Winres.exe ve Visual Studio

Genel olarak, bir uygulamanın Windows Forms formlarını yerelleştirmeye başlamadan önce, yerelleştirme aracı olarak Visual Studio'yu mu yoksa Winres.exe'yi mi kullanmak istediğinize karar vermelisiniz. Sürüm uyumluluğu, daha sonra açıklandığı gibi, bir araçtan diğerine geçiş yapmasını engelleyebilir.

Visual Studio'nun avantajı, bir uygulamayı hem geliştirmek hem de yerelleştirmek için kullanabilmenizdedir. Bir formu yerelleştirmek için, geliştirme tamamlandıktan sonra, <xref:System.ComponentModel.LocalizableAttribute> formun **(Özellikler** düzenleyicisindeki `true` **Yerelleştirilebilir** özellik) ayarlayın ve **Dil** özelliğini istenilen hedef kültüre değiştirin. Daha sonra, dizeleri düzenleyin ve denetimlerin konumu ile boyutunu hedef kültürün dizelerine uygun olacak şekilde ayarlayın. Yerelleştirilmiş .resx dosyasını kaydettiğinizde, Visual Studio dosyaya yalnızca yerelleştirilebilir özellikleri (hedef kültürde değiştirilen özellikler) yazar. Visual Studio, yerelleştirilmiş .resx dosyası için bir uydu derlemesini doğru dizin konumunda otomatik olarak oluşturur.

Visual Studio entegre bir geliştirme ve yerelleştirme ortamı sağlasa da, yerelleştirme üçüncü taraf yerelleştiriciler tarafından yapılıyorsa Winres.exe kullanılması önerilen araçtır. Winres.exe yalnızca bir yerelleştirme aracı olduğu için, bir uygulamanın kodu ile yerelleştirilecek formlar arasında daha net bir ayrım sağlar, ki bu da büyük projeleri yönetirken daha büyük bir kolaylık demektir.

## <a name="using-winresexe"></a>Winres.exe'yi kullanma

Winres.exe'yi kullanarak yerelleştirmek için öncelikle Visual Studio'daki **Windows Forms Designer** gibi görsel bir tasarımcıyı kullanarak bir uygulama geliştirmeniz gerekir. Geliştirme tamamlandığında, <xref:System.ComponentModel.LocalizableAttribute> formun **(Özellikler** düzenleyicisindeki **Yerelleştirilebilir** özellik) `true`formunu ayarlayın ve varsayılan kültür için .resx dosyasını üçüncü taraf yerelleştiriciye teslim edin. Bu .resx dosyası özgün formun tasarım zamanı sürümünü yeniden oluşturmak için Winres.exe'nin kullandığı ek bilgileri içerir.

> [!NOTE]
> Winres.exe varsayılan kaynak dosyayı düzenlemek için kullanılamaz. Winres.exe, değişen tüm özellikleri yerelleştirilmiş özellikler olarak yorumlar ve bunları hedef kültür kaynak dosyasına kaydeder.

Kültür kaynak dosyalarının son sürümleri son olarak uygulamanın yerelleştirilmiş sürümlerini oluşturmak için kullanılabilir. Daha fazla bilgi için [Masaüstü Uygulamalarındaki Kaynaklar'a](../resources/index.md)bakın.

Winres.exe aşağıdaki özelliklere ve yeteneklere sahiptir:

- Winres Tek Dosya Modu'nda (SFM) veya Visual Studio Dosya Modu'nda (VSFM) çalışabilir. SFM, form ve içeriği hakkındaki tüm bilgilerin kaynak dosyada depolandığı eski moddur. VSFM kültürel değişiklikleri yalnızca kaynak dosyasında depolar.

- Ana pencerenin sol alt bölümüne sabitlenmiş bir hata raporlama penceresi.

- Eşara tuşlar yinelenenler için kontrol edilebilir: **Biçim** menüsünden, **Tuştuşlarını Kontrol Et** komutunu tıklatın.

## <a name="version-compatibility"></a>Sürüm Uyumluluğu

Kullanmakta olduğunuz .NET Framework ile piyasaya sürülen Winres.exe sürümünü kullanmalısınız. Aşağıdaki tabloda uyumlu sürümler listelenebilmiştir:

|Visual Studio|.NET Framework|Winres.exe|
|-------------------|--------------------|----------------|
|Görsel Stüdyo .NET 2002|1.0|1.0|
|Visual Studio .NET 2003|1.1|1.1|
|Visual Studio 2005|2,0|2,0|
|Visual Studio 2008|3.0 ve 3.5|3.0 ve 3.5|
|Visual Studio 2010|4.0|4.0|
|Visual Studio 2017|4.6|4.6|

> [!NOTE]
> VSFM'de, Visual Studio ile uyumluluk avantajı bulunuyor olsa da, kaynak dosyaya yalnızca değiştirilmiş değerleri depoladığından, Winres.exe geçerli kaynak dosyanın üst öğelerinin aynı dizinde bulunmasını gerektirir. Örneğin, düzenleme `TestApp.de-DE.resources`, Almanya'da bir Alman kaynak dosyası, varsayılan `TestApp.resx`kaynak dosyasının varlığını gerektirir, `TestApp.de.resources`ve muhtemelen kültürden bağımsız kaynak dosyası, .

## <a name="examples"></a>Örnekler

### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Bir formla ilişkili .resx veya .resources dosyasını yerelleştirmek için

1. Winres.exe çalıştırmak için geliştirici komut istemi yazın. `winres`

2. Bir formun yerelleştirilmesi için varsayılan kaynakları açmak için **Dosya** menüsündeki **Aç** komutunu tıklatın ve açmak için dosyaya gidin.

     -veya-

     Winres.exe'yi başlattığınızda komut satırında açılacak dosyayı belirtin.

     Aşağıdaki komut Winres.exe'yi başlatır `TestApp.resx` ve Form Tasarımcısı'nda ilişkili formu yükler.

    ```console
    winres TestApp.resx
    ```

     Aşağıdaki komut Winres.exe'yi başlatır `TestApp.resources` ve Form Tasarımcısı'nda ilişkili formu yükler.

    ```console
    winres TestApp.resources
    ```

    > [!NOTE]
    > Kaynaklarını düzenlediğiniz form devralınmış bir form ise, hem formun içindeki derleme hem de devralan (türetilmiş) formu içeren derleme Genel Derleme Önbelleği'ne (GAC) kaydettirilmeli veya WinRes.exe ile aynı dizinde bulunmalıdır. .NET Framework bileşenlerinin GAC'ye yüklenmesi hakkında daha fazla bilgi için [Bkz.](../app-domains/gac.md)

3. Form üzerindeki denetimleri seçin <xref:System.Windows.Forms.Control.Text%2A> ve yerelleştirilmiş kültürü ve dilini yansıtacak şekilde bunların ve diğer özelliklerinin değiştirin. Yerelleştirilmiş metnin sığmasını sağlayacak şekilde denetimleri gerektiği gibi taşıyın veya yeniden boyutlandırın.

4. .resx veya .resources dosyasının yerelleştirilmiş sürümünü kaydetmek için **Dosya** menüsünde **Kaydet** simgesini veya aynı komutu tıklatın. Araç Kültür **Seç** penceresini görüntüler.

5. Uygun kültür ve dosya modunu seçin ve **ardından Tamam'ı**tıklatın.

   Araç, çalışma süresinin yerelleştirilmiş kaynak dosyaları için beklediği adlandırma kuralını kullanarak dosyayı kaydeder. Örneğin, Almanya'da `TestApp.resources` Almanca için yerelleştirirseniz, araç dosyayı `TestApp.de-DE.resources`. Almanya'da `TestApp.resx` Almanca için yerelleştirirseniz, araç dosyayı `TestApp.de-DE.resx`. Kaynak adlandırma kuralları hakkında daha fazla bilgi için [bkz.](../resources/packaging-and-deploying-resources-in-desktop-apps.md) Çalışma zamanı tarafından kullanılan önceden tanımlanmış kültür adlarının <xref:System.Globalization.CultureInfo> listesi için sınıfa bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.LocalizableAttribute>
- <xref:System.Globalization.CultureInfo>
- <xref:System.Resources.ResourceManager>
- <xref:System.Resources.ResourceReader>
- <xref:System.Resources.ResourceWriter>
- [Araçlar](index.md)
- [Masaüstü Uygulamalarında Kaynaklar](../resources/index.md)
- [Genelleştirme ve Yerelleştirme](../../standard/globalization-localization/index.md)
