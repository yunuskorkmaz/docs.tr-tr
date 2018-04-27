---
title: Çok sınıftan geçirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
caps.latest.revision: 3
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 09d982105d8cf1297a53bd755003e3ef2b089293
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="migrating-from-the-xsltransform-class"></a>Çok sınıftan geçirme
XSLT mimari olarak tasarlandığından [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] serbest bırakın. <xref:System.Xml.Xsl.XslTransform> Sınıfı tarafından değiştirildi <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
 Aşağıdaki bölümlerde bazı arasındaki farklar açıklanmaktadır <xref:System.Xml.Xsl.XslCompiledTransform> ve <xref:System.Xml.Xsl.XslTransform> sınıfları.  
  
## <a name="performance"></a>Performans  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, birçok performans iyileştirmeleri içerir. Yeni XSLT işlemci ortak Ara benzer bir biçimde, ortak dil çalışma zamanı (CLR) başka bir programlama dili için yaptığı için aşağıya doğru XSLT stil sayfası derler. Stil sayfası derlenmiş sonra önbelleğe alınmış ve yeniden kullanılabilir.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı ayrıca çok daha hızlı hale diğer en iyi duruma getirmeleri içerir <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
> [!NOTE]
>  Ancak genel performansını <xref:System.Xml.Xsl.XslCompiledTransform> sınıftır daha iyi <xref:System.Xml.Xsl.XslTransform> sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı daha gerçekleştirebileceğiniz daha yavaş <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslTransform> sınıfı ilk kez üzerinde dönüştürme adı verilir. XSLT dosyasının yüklendiği önce derlenmelidir olmasıdır. Daha fazla bilgi için aşağıdaki blog gönderisine bakın: [XslCompiledTransform çok daha yavaş?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="security"></a>Güvenlik  
 Varsayılan olarak, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, XSLT desteğini devre dışı bırakır `document()` işlevi ve katıştırılmış komut dosyası. Bu özellikler oluşturarak etkin hale getirilebilir bir <xref:System.Xml.Xsl.XsltSettings> etkin ve kendisine geçirme özelliklere sahip nesne <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi. Aşağıdaki örnek, betik kullanımını etkinleştirmek ve XSLT dönüşümü gerçekleştirmeye gösterilmektedir.  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 Daha fazla bilgi için bkz: [XSLT güvenlik konuları](../../../../docs/standard/data/xml/xslt-security-considerations.md).  
  
## <a name="new-features"></a>Yeni Özellikler  
  
### <a name="temporary-files"></a>Geçici dosyalar  
 Geçici dosyalar bazen XSLT sırasında oluşturulan işleniyor. Stil sayfası komut dosyası blokları içeriyorsa ya da hata ayıklama ayar ile derlenmiş ise true, geçici dosyaları % TEMP % klasöründe oluşturulabilir. Bazı geçici dosyaları zamanlama sorunları nedeniyle silinmez örnekleri olabilir. Örneğin, dosyaları geçerli AppDomain veya sonlandırıcıyı, hata ayıklayıcı tarafından kullanılıyorsa <xref:System.CodeDom.Compiler.TempFileCollection> nesne bunları kaldırmak mümkün olmayacak.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Özelliği tüm geçici dosyaların istemciden kaldırıldığından emin olmak için ek Temizleme için kullanılabilir.  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Öğe önceliğiyle desteği ve XmlWriter  
 <xref:System.Xml.Xsl.XslTransform> Göz ardı sınıfı `xsl:output` dönüştürme çıkış gönderildiği ayarlarını bir <xref:System.Xml.XmlWriter> nesnesi. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfına sahip bir <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> döndüren özelliği bir <xref:System.Xml.XmlWriterSettings> çıktı bilgilerini içeren bir nesne türetilen `xsl:output` stil sayfası öğesidir. <xref:System.Xml.XmlWriterSettings> Nesnesi oluşturmak için kullanılan bir <xref:System.Xml.XmlWriter> nesne için geçirilen doğru ayarlarla <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi. Aşağıdaki C# kod bu davranış gösterir:  
  
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
  
### <a name="debug-option"></a>Debug seçeneği  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, Microsoft ile stil sayfası ayıklamanızı sağlar hata ayıklama bilgileri üretebilir [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] hata ayıklayıcı. Daha fazla bilgi edinmek için bkz. <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.  
  
## <a name="behavioral-differences"></a>Davranış farklılıkları  
  
### <a name="transforming-to-an-xmlreader"></a>XmlReader değerine dönüştürme  
 <xref:System.Xml.Xsl.XslTransform> Sınıfına sahip olarak dönüşüm sonuçları döndüren birkaç dönüştürme aşırı bir <xref:System.Xml.XmlReader> nesnesi. Bu aşırı yük bir bellek içi gösterimine dönüşüm sonuçları için kullanılabilir (gibi <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument>) yükü serileştirme ve seri durumundan çıkarma sonuç XML yansıtılmasını olmadan ağacı. Aşağıdaki C# kodu yük içine dönüşüm sonuçları gösterilmektedir bir <xref:System.Xml.XmlDocument> nesnesi.  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı için dönüştürme desteklemiyor bir <xref:System.Xml.XmlReader> nesnesi. Ancak, bunu tarafından benzer bir şey kullanarak yapabilirsiniz <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> sonuç XML yüklenmedi yöntemi ağaç doğrudan bir <xref:System.Xml.XmlWriter>. Aşağıdaki C# kodu kullanarak aynı görevi gerçekleştirmenin gösterilmiştir <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a>İsteğe bağlı davranışı  
 W3C XSL Dönüşümleri (XSLT) sürüm 1.0 öneri uygulama sağlayıcısı bir durumu işlemek nasıl karar verebilir alanları içerir. Bu alanlar isteğe bağlı davranış olduğu kabul edilir. Bazı alanlar vardır nerede <xref:System.Xml.Xsl.XslCompiledTransform> daha farklı şekilde davranan <xref:System.Xml.Xsl.XslTransform> sınıfı. Daha fazla bilgi için bkz: [kurtarılabilir XSLT hataları](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).  
  
### <a name="extension-objects-and-script-functions"></a>Uzantı nesneleri ve komut dosyası işlevleri  
 <xref:System.Xml.Xsl.XslCompiledTransform> iki yeni kullanma kısıtlamaları betik işlevleri sunar:  
  
-   Yalnızca genel yöntemleri gelen XPath ifadeleri çağrılabilir.  
  
-   Aşırı birbirinden bağımsız değişken sayısına göre ayrılabilen. Birden fazla aşırı yüklemesiyle aynı sayıda bağımsız değişken varsa, bir özel durum oluşturulur.  
  
 İçinde <xref:System.Xml.Xsl.XslCompiledTransform>derleme zamanında komut dosyası işlevlerinin bir bağlama (yöntemi adı arama) oluşur ve XslTranform ile çalışılan stil sayfaları neden olabilir. özel durum ile yüklenen olduklarında <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> destekleyen sahip `msxsl:using` ve `msxsl:assembly` alt öğelerin `msxsl:script` öğesi. `msxsl:using` Ve `msxsl:assembly` öğeleri ek ad alanları ve derlemeler betik bloğundaki kullanılmak bildirmek için kullanılır. Bkz: [komut dosyası blokları kullanarak msxsl: Script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) daha fazla bilgi için.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> ile aynı sayıda bağımsız değişken birden çok aşırı uzantısı nesneleri engelliyor.  
  
### <a name="msxml-functions"></a>MSXML işlevleri  
 Ek MSXML işlevleri için eklenene desteği <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Aşağıdaki listede, yeni veya geliştirilmiş işlevselliği açıklanmaktadır:  
  
-   msxsl:node-ayarlayın: <xref:System.Xml.Xsl.XslTransform> bağımsız değişkeni gerekli [düğüm kümesi işlevi](https://msdn.microsoft.com/library/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) işlevi sonuç ağacı parçası olabilir. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı bu gereksinime sahip değil.  
  
-   msxsl:Version: Bu işlev desteklenir <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   XPath uzantı işlevleri: [ms:string-compare işlevi](https://msdn.microsoft.com/library/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc işlevi](https://msdn.microsoft.com/library/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace-URI işlevi](https://msdn.microsoft.com/library/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local-işleviadı](https://msdn.microsoft.com/library/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number işlevi](https://msdn.microsoft.com/library/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-işlevi tarih](https://msdn.microsoft.com/library/51f35609-89a9-4098-a166-88bf01300bf5), ve [ms:format-işlevi zaman](https://msdn.microsoft.com/library/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) işlevleri artık desteklenmektedir.  
  
-   Şema ilgili XPath uzantısı işlevleri: Bu işlevler tarafından yerel olarak desteklenmeyen <xref:System.Xml.Xsl.XslCompiledTransform>. Ancak, uzantı işlevleri uygulanabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
