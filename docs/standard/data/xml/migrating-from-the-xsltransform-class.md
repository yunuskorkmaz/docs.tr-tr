---
title: XslTransform sınıfından geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8b8c21af8ca0a21d97e8246ad82c42aaaf4974
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190994"
---
# <a name="migrating-from-the-xsltransform-class"></a>XslTransform sınıfından geçirme
XSLT mimari olarak tasarlandı [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] bırakın. <xref:System.Xml.Xsl.XslTransform> Sınıfı tarafından değiştirilmiştir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
 Aşağıdaki bölümlerde ana farklılıklar açıklanmaktadır <xref:System.Xml.Xsl.XslCompiledTransform> ve <xref:System.Xml.Xsl.XslTransform> sınıfları.  
  
## <a name="performance"></a>Performans  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, çok sayıda performans iyileştirmeleri içerir. Yeni XSLT işlemci XSLT stil sayfası ortak Ara benzer bir biçimde, ortak dil çalışma zamanı (CLR) diğer programlama dili için yaptığı için aşağı derler. Stil sayfası derlenmiş sonra önbelleğe alınan ve yeniden.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı da çok daha hızlı hale diğer iyileştirmeler içerir <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
> [!NOTE]
>  Ancak genel performansını <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, daha iyi <xref:System.Xml.Xsl.XslTransform> sınıfı <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı daha gerçekleştirebileceğiniz daha yavaş <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslTransform> sınıfı ilk kez bir dönüştürme üzerinde çağrılır. XSLT dosyası, yüklenmeden önce derlenmesi gereken olmasıdır. Daha fazla bilgi için bkz şu blog gönderisi: [XslCompiledTransform XslTransform daha yavaş?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="security"></a>Güvenlik  
 Varsayılan olarak, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT desteğini devre dışı bırakır `document()` işlevi ve katıştırılmış betik oluşturma. Bu özellikler oluşturarak etkin hale getirilebilir bir <xref:System.Xml.Xsl.XsltSettings> aktarması ve etkinleştirilen özellikleri nesnesi <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi. Aşağıdaki örnek komut dosyası yazmayı etkinleştirin ve XSLT dönüşümü gerçekleştirmek nasıl gösterir.  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 Daha fazla bilgi için [XSLT güvenlik konuları](../../../../docs/standard/data/xml/xslt-security-considerations.md).  
  
## <a name="new-features"></a>Yeni Özellikler  
  
### <a name="temporary-files"></a>Geçici dosyalar  
 Geçici dosyalar bazen XSLT sırasında oluşturulan işleme. Komut dosyası blokları bir stil sayfası içeriyorsa, ya da hata ayıklama ayar ile derlenmiş ise true, geçici dosyaları % TEMP % klasöründe oluşturulabilir. Zamanlama sorunları nedeniyle bazı geçici dosyaları silinmez örnekleri olabilir. Örneğin, dosyaların geçerli AppDomain veya sonlandırıcının çalışmasının hata ayıklayıcı tarafından kullanılıyorsa <xref:System.CodeDom.Compiler.TempFileCollection> nesne kaldırmak mümkün olmayacaktır.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Özelliği tüm geçici dosyaları istemciden kaldırıldığından emin emin olmak için ek Temizleme için kullanılabilir.  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Öğe önceliğiyle desteği ve XmlWriter  
 <xref:System.Xml.Xsl.XslTransform> Sınıf göz ardı `xsl:output` dönüştürme çıkış gönderildiği zaman ayarları bir <xref:System.Xml.XmlWriter> nesne. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfında bir <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> döndüren özellik bir <xref:System.Xml.XmlWriterSettings> çıkış bilgileri içeren bir nesne türetilen `xsl:output` stil sayfası öğesi. <xref:System.Xml.XmlWriterSettings> Nesne oluşturmak için kullanılan bir <xref:System.Xml.XmlWriter> nesne geçirilebilir doğru ayarlarla <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi. Bu davranışı aşağıdaki C# kodunu göstermektedir:  
  
```  
// Create the XslTransform object and load the style sheet.  
XslCompiledTransform xslt = new XslCompiledTransform();  
xslt.Load(stylesheet);  
  
// Load the file to transform.  
XPathDocument doc = new XPathDocument(filename);  
  
// Create the writer.  
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);  
  
// Transform the file and send the output to the console.  
xslt.Transform(doc, writer);  
writer.Close();  
```  
  
### <a name="debug-option"></a>Hata ayıklama seçeneği  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıf Microsoft Visual Studio hata ayıklayıcısı ile stil sayfasında hata ayıklama olanak tanıyan hata ayıklama bilgilerini oluşturabilir. Daha fazla bilgi edinmek için bkz. <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.  
  
## <a name="behavioral-differences"></a>Davranışsal farklılıklar  
  
### <a name="transforming-to-an-xmlreader"></a>XmlReader'a dönüştürme  
 <xref:System.Xml.Xsl.XslTransform> Sınıfında dönüştürme sonuç olarak döndüren birkaç dönüştürme aşırı yüklemeler bir <xref:System.Xml.XmlReader> nesne. Bu aşırı yüklemeler bir bellek içi gösterimine dönüştürme sonuç yüklemek için kullanılabilir (gibi <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument>) ek yükü serileştirme ve seri durumundan çıkarma elde edilen XML ödemeden ağaç. Aşağıdaki C# kodu dönüştürme sonuçlara yüklenecek gösterilmiştir bir <xref:System.Xml.XmlDocument> nesne.  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı için dönüştürme desteklemiyor bir <xref:System.Xml.XmlReader> nesne. Ancak, bunu tarafından benzer bir şey kullanarak yapabilirsiniz <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> elde edilen XML yüklemek için gereken yöntemini ağaç doğrudan bir <xref:System.Xml.XmlWriter>. Aşağıdaki C# kodunu kullanarak aynı görevi yerine getirmeyi gösterir <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a>İsteğe bağlı davranışı  
 W3C XSLT Dönüşümleri (XSLT) sürüm 1.0 öneri uygulama sağlayıcısı bir durumu işlemek nasıl karar verebilir alanları içerir. Bu alanlar isteğe bağlı bir davranış olarak değerlendirilir. Çeşitli alanlar vardır burada <xref:System.Xml.Xsl.XslCompiledTransform> değerinden farklı davranır <xref:System.Xml.Xsl.XslTransform> sınıfı. Daha fazla bilgi için [kurtarılabilir XSLT hataları](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).  
  
### <a name="extension-objects-and-script-functions"></a>Genişletme nesneleri ve komut dosyası işlevleri  
 <xref:System.Xml.Xsl.XslCompiledTransform> betik işlevlerin kullanımına iki yeni kısıtlamaları getirir:  
  
-   Yalnızca genel yöntemleri gelen XPath ifadeleri çağrılabilir.  
  
-   Aşırı yüklemeler, birbirinden bağımsız değişken sayısına göre ayrılabilen. Birden fazla aşırı yükleme bağımsız değişkenleri aynı sayıda varsa, bir özel durum oluşturulur.  
  
 İçinde <xref:System.Xml.Xsl.XslCompiledTransform>, derleme zamanında betik işlevleri için bir bağlama (ad arama yöntemi) oluşur ve yüklü olduğunda, stil sayfaları, XslTranform ile çalışan bir özel durum neden olabilir <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> destekleyen sahip `msxsl:using` ve `msxsl:assembly` alt öğelerin `msxsl:script` öğesi. `msxsl:using` Ve `msxsl:assembly` öğeleri ek ad alanları ve derlemeler için betik bloğundaki kullanım bildirmek için kullanılır. Bkz: [msxsl: Script komut dosyası blokları kullanarak](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) daha fazla bilgi için.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> birden çok aşırı yükleme ile aynı sayıda bağımsız değişken olan uzantı nesneleri yasaklar.  
  
### <a name="msxml-functions"></a>MSXML işlevleri  
 Ek MSXML işlevler için eklenmiştir desteği <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Aşağıdaki listede, yeni veya geliştirilmiş işlevselliği açıklanmaktadır:  
  
-   msxsl:node-ayarla: <xref:System.Xml.Xsl.XslTransform> bağımsız değişkeni gerekli [düğüm kümesi işlevi](https://msdn.microsoft.com/library/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) bir sonuç ağacı parçası işlevi. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı bu gereksinime sahip değil.  
  
-   msxsl:Version: Bu işlev desteklenen <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   XPath uzantı işlevleri: [ms:string-işlevi karşılaştırma](https://msdn.microsoft.com/library/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc işlevi](https://msdn.microsoft.com/library/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [MS: namespace-URI işlevi](https://msdn.microsoft.com/library/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local-işleviadı](https://msdn.microsoft.com/library/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number işlevi](https://msdn.microsoft.com/library/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-işlevi tarih](https://msdn.microsoft.com/library/51f35609-89a9-4098-a166-88bf01300bf5), ve [ms:format-işlevin zaman](https://msdn.microsoft.com/library/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) işlevleri artık desteklenmektedir.  
  
-   Şema ilgili XPath uzantı işlevleri: Bu işlevler tarafından yerel olarak desteklenmeyen <xref:System.Xml.Xsl.XslCompiledTransform>. Ancak, uzantı işlevleri uygulanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
