---
title: XslTransform Sınıfından Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 95e71e1fdd0ded145025316a5d6597b27a6cc970
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710654"
---
# <a name="migrating-from-the-xsltransform-class"></a>XslTransform Sınıfından Geçirme

XSLT mimarisi, Visual Studio 2005 sürümünde yeniden tasarlanmıştır. <xref:System.Xml.Xsl.XslTransform> sınıfı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfıyla değiştirilmiştir.

Aşağıdaki bölümlerde, <xref:System.Xml.Xsl.XslCompiledTransform> ve <xref:System.Xml.Xsl.XslTransform> sınıfları arasındaki temel farklılıklar açıklanır.

## <a name="performance"></a>Performans

<xref:System.Xml.Xsl.XslCompiledTransform> sınıfı birçok performans geliştirmesi içerir. Yeni XSLT işlemcisi, XSLT stil sayfasını, diğer programlama dilleri için ortak dil çalışma zamanının (CLR) yaptığı gibi ortak bir ara biçimde derler. Stil sayfası derlendikten sonra, önbelleğe alınmış ve yeniden kullanılabilir.

<xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, <xref:System.Xml.Xsl.XslTransform> sınıfından çok daha hızlı hale getirmek için diğer iyileştirmeler de içerir.

> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> sınıfının genel performansı <xref:System.Xml.Xsl.XslTransform> sınıfından daha iyidir, ancak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfının <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi, bir dönüşümde ilk kez çağrıldığında <xref:System.Xml.Xsl.XslTransform.Load%2A> sınıfının <xref:System.Xml.Xsl.XslTransform> yönteminden daha yavaş çalışabilir. Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir. Daha fazla bilgi için şu blog gönderisine bakın: [XslCompiledTransform, XslTransform 'Dan daha yavaş?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)

## <a name="security"></a>Güvenlik

Varsayılan olarak, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT `document()` işlevi ve katıştırılmış komut dosyası desteğini devre dışı bırakır. Bu özellikler, etkinleştirilen özellikler içeren bir <xref:System.Xml.Xsl.XsltSettings> nesnesi oluşturularak ve <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine geçirerek etkinleştirilebilir. Aşağıdaki örnek, komut dosyasının nasıl etkinleştirileceğini ve XSLT dönüşümünün nasıl gerçekleştirileceğini gösterir.

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

Daha fazla bilgi için bkz. [XSLT güvenlik konuları](../../../../docs/standard/data/xml/xslt-security-considerations.md).

## <a name="new-features"></a>Yeni Özellikler

### <a name="temporary-files"></a>Geçici dosyalar

Geçici dosyalar bazen XSLT işleme sırasında üretilir. Bir stil sayfası betik blokları içeriyorsa veya hata ayıklama ayarı true olarak ayarlandıysa derlenmiş ise, geçici dosyalar% TEMP% klasöründe oluşturulabilir. Zamanlama sorunları nedeniyle bazı geçici dosyalar silinmediği durumlarda örnek olabilir. Örneğin, dosyalar geçerli AppDomain veya hata ayıklayıcı tarafından kullanılıyorsa, <xref:System.CodeDom.Compiler.TempFileCollection> nesnesinin sonlandırıcısı bunları kaldıramayacak.

<xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> özelliği, tüm geçici dosyaların istemciden kaldırıldığından emin olmak için ek temizleme işlemleri için kullanılabilir.

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Xsl: output öğesi ve XmlWriter desteği

<xref:System.Xml.Xsl.XslTransform> sınıfı, dönüşüm çıktısı bir <xref:System.Xml.XmlWriter> nesnesine gönderildiğinde ayarları `xsl:output` yok sayılır. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, stil sayfasının `xsl:output` öğesinden türetilmiş çıkış bilgilerini içeren bir <xref:System.Xml.XmlWriterSettings> nesnesi döndüren bir <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> özelliğine sahiptir. <xref:System.Xml.XmlWriterSettings> nesnesi, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirilebilecek doğru ayarlarla bir <xref:System.Xml.XmlWriter> nesnesi oluşturmak için kullanılır. Aşağıdaki C# kod bu davranışı göstermektedir:

```csharp
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

<xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, Microsoft Visual Studio hata ayıklayıcıyla stil sayfasında hata ayıklamanızı sağlayan hata ayıklama bilgileri oluşturabilir. Daha fazla bilgi edinmek için bkz. <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.

## <a name="behavioral-differences"></a>Davranış farkları

### <a name="transforming-to-an-xmlreader"></a>XmlReader 'a dönüştürme

<xref:System.Xml.Xsl.XslTransform> sınıfında, dönüştürme sonuçlarını bir <xref:System.Xml.XmlReader> nesnesi olarak döndüren birkaç dönüşüm aşırı yüklemesi vardır. Bu aşırı yüklemeler, elde edilen XML ağacının serileştirme ve serisini kaldırma yükünü ortadan kaldırmadan, dönüştürme sonuçlarını bellek içi bir gösterimine (<xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument>) yüklemek için kullanılabilir. Aşağıdaki C# kod, dönüştürme sonuçlarının bir <xref:System.Xml.XmlDocument> nesnesine nasıl yükleneceğini gösterir.

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<xref:System.Xml.Xsl.XslCompiledTransform> sınıfı bir <xref:System.Xml.XmlReader> nesnesine dönüştürmeyi desteklemiyor. Ancak, sonuçta elde edilen XML ağacını doğrudan bir <xref:System.Xml.XmlWriter>yüklemek için <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> yöntemini kullanarak benzer bir şey yapabilirsiniz. Aşağıdaki C# kod, <xref:System.Xml.Xsl.XslCompiledTransform>kullanarak aynı görevin nasıl gerçekleştirileceğini gösterir.

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a>İsteğe bağlı davranış

W3C XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi, uygulama sağlayıcısının bir durumu nasıl ele verileceğine karar vermesine olanak tanıyan bölgeleri içerir. Bu alanların kısıtlı davranış olduğu kabul edilir. <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform> sınıftan farklı davrandığı birkaç alan vardır. Daha fazla bilgi için bkz. [KURTARıLABILIR XSLT hataları](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).

### <a name="extension-objects-and-script-functions"></a>Uzantı nesneleri ve betik Işlevleri

<xref:System.Xml.Xsl.XslCompiledTransform>, betik işlevlerinin kullanımıyla ilgili iki yeni kısıtlama sunar:

- XPath ifadelerinden yalnızca ortak Yöntemler çağrılabilir.

- Aşırı Yüklemeler, bağımsız değişken sayısına göre birbirinden ayırt edilemez. Birden fazla aşırı yükleme aynı sayıda bağımsız değişkene sahipse, bir özel durum oluşturulur.

<xref:System.Xml.Xsl.XslCompiledTransform>, derleme zamanında betik işlevlerine bir bağlama (Yöntem adı araması) oluşur ve XslTransform ile çalışan stil sayfaları, <xref:System.Xml.Xsl.XslCompiledTransform>yüklendiğinde bir özel duruma neden olabilir.

<xref:System.Xml.Xsl.XslCompiledTransform>, `msxsl:script` öğesi içinde `msxsl:using` ve `msxsl:assembly` alt öğelerinin olmasını destekler. `msxsl:using` ve `msxsl:assembly` öğeleri, komut dosyası bloğunda kullanılmak üzere ek ad alanları ve derlemeler bildirmek için kullanılır. Daha fazla bilgi için bkz. [msxsl: script kullanarak betik blokları](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) .

<xref:System.Xml.Xsl.XslCompiledTransform>, aynı sayıda bağımsız değişkene sahip birden fazla aşırı yüküne sahip uzantı nesnelerini yasaklar.

### <a name="msxml-functions"></a>MSXML Işlevleri

<xref:System.Xml.Xsl.XslCompiledTransform> sınıfına ek MSXML işlevleri desteği eklenmiştir. Aşağıdaki listede yeni veya geliştirilmiş işlevler açıklanmaktadır:

- msxsl: node-set: <xref:System.Xml.Xsl.XslTransform> [düğüm kümesi işlev](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) işlevinin bağımsız değişkenini bir sonuç ağacı parçası olacak şekilde gerektirdi. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı bu gereksinime sahip değil.

- msxsl: Version: Bu işlev <xref:System.Xml.Xsl.XslCompiledTransform>desteklenir.

- XPath uzantı işlevleri: [MS: String-Compare işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: namespace-uri işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: yerel-adı işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number işlevi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), MS: [Format-Date](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))işlevi ve [MS: biçim-zamanı işlev](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) işlevleri artık desteklenmektedir.

- Şemaya ilişkin XPath uzantı işlevleri: Bu işlevler <xref:System.Xml.Xsl.XslCompiledTransform>tarafından yerel olarak desteklenmez. Ancak, uzantı işlevleri olarak uygulanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
- [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
