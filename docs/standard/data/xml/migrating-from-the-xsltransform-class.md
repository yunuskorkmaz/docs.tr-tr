---
title: XslTransform Sınıfından Geçirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: 32fac1b5ab339dd4c71d761cf07fcde99ce1f2fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550169"
---
# <a name="migrating-from-the-xsltransform-class"></a>XslTransform Sınıfından Geçirme

XSLT mimarisi, Visual Studio 2005 sürümünde yeniden tasarlanmıştır. <xref:System.Xml.Xsl.XslTransform>Sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfıyla değiştirilmiştir.

Aşağıdaki bölümlerde, ve sınıfları arasındaki bazı önemli farklılıklar açıklanır <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform> .

## <a name="performance"></a>Performans

<xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı birçok performans geliştirmesi içerir. Yeni XSLT işlemcisi, XSLT stil sayfasını, diğer programlama dilleri için ortak dil çalışma zamanının (CLR) yaptığı gibi ortak bir ara biçimde derler. Stil sayfası derlendikten sonra, önbelleğe alınmış ve yeniden kullanılabilir.

<xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, sınıfından çok daha hızlı hale gelen diğer iyileştirmeler da içerir <xref:System.Xml.Xsl.XslTransform> .

> [!NOTE]
> Sınıfının genel performansı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfından daha iyidir <xref:System.Xml.Xsl.XslTransform> , ancak <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> sınıfın yöntemi, <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.Xsl.XslTransform> bir dönüşümde ilk kez çağrıldığında sınıfının yönteminden daha yavaş çalışabilir. Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir. Daha fazla bilgi için şu blog gönderisine bakın: [XslCompiledTransform, XslTransform 'Dan daha yavaş?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)

## <a name="security"></a>Güvenlik

Varsayılan olarak, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı XSLT `document()` işlevi ve katıştırılmış komut dosyası desteğini devre dışı bırakır. Bu özellikler, <xref:System.Xml.Xsl.XsltSettings> özelliği etkinleştirilmiş ve yöntemine geçen bir nesne oluşturularak etkinleştirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> . Aşağıdaki örnek, komut dosyasının nasıl etkinleştirileceğini ve XSLT dönüşümünün nasıl gerçekleştirileceğini gösterir.

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

Daha fazla bilgi için bkz. [XSLT güvenlik konuları](xslt-security-considerations.md).

## <a name="new-features"></a>Yeni Özellikler

### <a name="temporary-files"></a>Geçici dosyalar

Geçici dosyalar bazen XSLT işleme sırasında üretilir. Bir stil sayfası betik blokları içeriyorsa veya hata ayıklama ayarı true olarak ayarlandıysa derlenmiş ise, geçici dosyalar% TEMP% klasöründe oluşturulabilir. Zamanlama sorunları nedeniyle bazı geçici dosyalar silinmediği durumlarda örnek olabilir. Örneğin, dosyalar geçerli AppDomain veya hata ayıklayıcı tarafından kullanılıyorsa, nesne sonlandırıcısı <xref:System.CodeDom.Compiler.TempFileCollection> bunları kaldıramayacak.

<xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A>Özelliği, tüm geçici dosyaların istemciden kaldırıldığından emin olmak için ek temizleme işlemleri için kullanılabilir.

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Xsl: output öğesi ve XmlWriter desteği

<xref:System.Xml.Xsl.XslTransform> `xsl:output` Dönüştürme çıktısı bir nesneye gönderildiğinde, sınıfı yoksayılan ayarları yok sayılır <xref:System.Xml.XmlWriter> . <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> <xref:System.Xml.XmlWriterSettings> stil sayfası öğesinden türetilmiş çıkış bilgilerini içeren bir nesne döndüren bir özelliğe sahiptir `xsl:output` . <xref:System.Xml.XmlWriterSettings>Nesnesi, <xref:System.Xml.XmlWriter> yöntemine geçirilebilecek doğru ayarlarla bir nesne oluşturmak için kullanılır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> . Aşağıdaki C# kodu bu davranışı göstermektedir:

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

<xref:System.Xml.Xsl.XslCompiledTransform>Sınıf, Microsoft Visual Studio hata ayıklayıcı ile stil sayfasında hata ayıklamanızı sağlayan hata ayıklama bilgileri oluşturabilir. Daha fazla bilgi edinmek için bkz. <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.

## <a name="behavioral-differences"></a>Davranış farkları

### <a name="transforming-to-an-xmlreader"></a>XmlReader 'a dönüştürme

<xref:System.Xml.Xsl.XslTransform>Sınıfında bir nesne olarak dönüştürme sonuçlarını döndüren birkaç dönüşüm aşırı yüklemesi vardır <xref:System.Xml.XmlReader> . Bu aşırı yüklemeler, <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> elde edilen XML ağacının serileştirme ve serisini kaldırma yükünü ortadan kaldırmadan, dönüştürme sonuçlarını bellek içi bir gösterimine (veya gibi) yüklemek için kullanılabilir. Aşağıdaki C# kodu, dönüştürme sonuçlarının bir nesnesine nasıl yükleneceğini gösterir <xref:System.Xml.XmlDocument> .

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<xref:System.Xml.Xsl.XslCompiledTransform>Sınıf, bir nesneye dönüştürmeyi desteklemiyor <xref:System.Xml.XmlReader> . Ancak, <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> elde EDILEN xml ağacını doğrudan bir öğesinden yüklemek için yöntemini kullanarak benzer bir şey yapabilirsiniz <xref:System.Xml.XmlWriter> . Aşağıdaki C# kodu, kullanılarak aynı görevin nasıl gerçekleştirileceğini gösterir <xref:System.Xml.Xsl.XslCompiledTransform> .

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a>İsteğe bağlı davranış

W3C XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi, uygulama sağlayıcısının bir durumu nasıl ele verileceğine karar vermesine olanak tanıyan bölgeleri içerir. Bu alanların kısıtlı davranış olduğu kabul edilir. <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfından farklı davrandığı birkaç alan vardır <xref:System.Xml.Xsl.XslTransform> . Daha fazla bilgi için bkz. [KURTARıLABILIR XSLT hataları](recoverable-xslt-errors.md).

### <a name="extension-objects-and-script-functions"></a>Uzantı nesneleri ve betik Işlevleri

<xref:System.Xml.Xsl.XslCompiledTransform> betik işlevlerinin kullanımıyla ilgili iki yeni kısıtlama sunar:

- XPath ifadelerinden yalnızca ortak Yöntemler çağrılabilir.

- Aşırı Yüklemeler, bağımsız değişken sayısına göre birbirinden ayırt edilemez. Birden fazla aşırı yükleme aynı sayıda bağımsız değişkene sahipse, bir özel durum oluşturulur.

' De <xref:System.Xml.Xsl.XslCompiledTransform> , derleme zamanında betik işlevlerine bir bağlama (Yöntem adı araması) oluşur ve XslTransform ile çalışan stil sayfaları, ile yüklendiğinde bir özel duruma neden olabilir <xref:System.Xml.Xsl.XslCompiledTransform> .

<xref:System.Xml.Xsl.XslCompiledTransform>`msxsl:using` `msxsl:assembly` öğesi içinde ve alt öğelerini destekler `msxsl:script` . `msxsl:using`Ve `msxsl:assembly` öğeleri, komut dosyası bloğunda kullanılmak üzere ek ad alanları ve derlemeler bildirmek için kullanılır. Daha fazla bilgi için bkz. [msxsl: script kullanarak betik blokları](script-blocks-using-msxsl-script.md) .

<xref:System.Xml.Xsl.XslCompiledTransform> aynı sayıda bağımsız değişkene sahip birden fazla aşırı yüklemesi olan uzantı nesnelerini yasaklar.

### <a name="msxml-functions"></a>MSXML Işlevleri

Sınıfa ek MSXML işlevleri desteği eklenmiştir <xref:System.Xml.Xsl.XslCompiledTransform> . Aşağıdaki listede yeni veya geliştirilmiş işlevler açıklanmaktadır:

- msxsl: node-set: <xref:System.Xml.Xsl.XslTransform> [düğüm kümesi işlev](/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) işlevinin bağımsız değişkeni bir sonuç ağacı parçası olacak şekilde gereklidir. <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfta bu gereksinim yoktur.

- msxsl: Version: Bu işlev ' de desteklenir <xref:System.Xml.Xsl.XslCompiledTransform> .

- XPath uzantı işlevleri: [MS: String-Compare işlevi](/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC işlevi](/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: namespace-uri işlevi](/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: yerel-adı işlevi](/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number işlevi](/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), MS: [Format-Date](/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))işlevi ve [MS: biçim-zamanı işlev](/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) işlevleri artık desteklenmektedir.

- Şemaya ilişkin XPath uzantı işlevleri: Bu işlevler tarafından yerel olarak desteklenmez <xref:System.Xml.Xsl.XslCompiledTransform> . Ancak, uzantı işlevleri olarak uygulanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](xslt-transformations.md)
- [XslCompiledTransform Sınıfını Kullanma](using-the-xslcompiledtransform-class.md)
