---
title: DataSet ve XmlDataDocument Eşitlemesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 3bbe28423385cae0f09f301c03b2b1a59edf101d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205062"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a>DataSet ve XmlDataDocument Eşitlemesi
ADO.net <xref:System.Data.DataSet> , size verilerin ilişkisel bir gösterimini sağlar. Hiyerarşik veri erişimi için .NET Framework bulunan XML sınıflarını kullanabilirsiniz. Geçmişte, bu iki veri gösterimi ayrı olarak kullanılmıştır. Ancak .NET Framework, veri **kümesi** nesnesi ve <xref:System.Xml.XmlDataDocument> nesnesi aracılığıyla hem ilişkisel hem de verilerin hiyerarşik temsillerine gerçek zamanlı, zaman uyumlu erişim sağlar.  
  
 Bir **veri kümesi** bir **XmlDataDocument**ile eşitlendiğinde, her iki nesne de tek bir veri kümesiyle çalışır. Bu, **veri kümesinde**bir değişiklik yapılırsa, değişikliğin **XmlDataDocument**'te yansıtıldığı ve tam tersi anlamına gelir. Veri kümesi ile **XmlDataDocument** arasındaki ilişki, tek bir veri kümesini kullanarak tek bir uygulamaya izin vererek çok sayıda esneklik oluşturur ve veri kümesinin tamamında (Web Forms gibi) yerleşik olarak bulunan tüm hizmet paketine erişebilir. Windows Forms denetimleri ve Visual Studio .NET tasarımcıları), ayrıca Genişletilebilir Stil sayfası dili (XSL), XSL dönüştürmeleri (XSLT) ve XML yol dili (XPath) dahil XML Hizmetleri paketi. Uygulamayla hedeflediğiniz hizmet kümesini seçmeniz gerekmez; her ikisi de mevcuttur.  
  
 Bir **veri kümesini** **XmlDataDocument**ile eşzamanlı hale getirmek için kullanabileceğiniz çeşitli yollar vardır. Şunları yapabilirsiniz:  
  
- Bir **veri kümesini** şema (yani, ilişkisel bir yapı) ve verilerle doldurun ve ardından yeni bir **XmlDataDocument**ile eşitler. Bu, varolan ilişkisel verilerin hiyerarşik bir görünümünü sağlar. Örneğin:  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
- Bir **veri kümesini** yalnızca şemayla (türü kesin belirlenmiş bir **veri kümesi**) doldurun, bir **XmlDataDocument**ile eşitler ve ardından bir XML belgesinden **XmlDataDocument** öğesini yükleyin. Bu, varolan hiyerarşik verilerin ilişkisel bir görünümünü sağlar. **Veri kümesi** şemanızın tablo adları ve sütun adları, EŞITLENMESINI istediğiniz XML öğelerinin adlarıyla eşleşmelidir. Bu eşleştirme, büyük/küçük harfe duyarlıdır.  
  
     **Veri kümesi** şemasının yalnızca ilişkisel görünüminizdeki göstermek istediğiniz XML öğeleriyle eşleşmesi gerektiğini unutmayın. Bu şekilde, bu belgede çok büyük bir XML belgeniz ve çok küçük bir ilişkisel "pencere" olabilir. **Veri kümesi** yalnızca küçük bir kısmını kullanıma sunsa, **XmlDataDocument** tüm XML belgesini korur. (Bunun ayrıntılı bir örneği için bkz. [bir veri kümesini XmlDataDocument Ile eşitleme](synchronizing-a-dataset-with-an-xmldatadocument.md).)  
  
     Aşağıdaki kod örneği, bir **veri kümesi** oluşturma ve şemasını doldurma ve sonra onu bir **XmlDataDocument**ile eşitleme adımlarını gösterir. **Veri kümesi** şemasının yalnızca **veri kümesini**kullanarak sergilemek istediğiniz **XmlDataDocument** nesnesinden öğelerle eşleşmesi gerektiğini unutmayın.  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     Veri içeren bir veri **kümesiyle** eşitlendiğinde **XmlDataDocument** ' i yükleyemezsiniz. Bir özel durum oluşturulur.  
  
- Yeni bir **XmlDataDocument** oluşturun ve bunu bir XML belgesinden yükleyin ve ardından **XmlDataDocument**'in **DataSet** özelliğini kullanarak verilerin ilişkisel görünümüne erişin. Veri **kümesini**kullanarak **XmlDataDocument** 'teki herhangi bir veriyi görüntüleyebilmeniz için veri **kümesinin** şemasını ayarlamanız gerekir. Yine, **veri kümesi** şemanızda tablo adları ve sütun adları, EŞITLENMELERINI istediğiniz XML öğelerinin adlarıyla eşleşmelidir. Bu eşleştirme, büyük/küçük harfe duyarlıdır.  
  
     Aşağıdaki kod örneğinde, bir **XmlDataDocument**'teki verilerin ilişkisel görünümüne nasıl erişebileceğiniz gösterilmektedir.  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 Bir **XmlDataDocument** Ile bir **veri kümesiyle** eşitlemenin başka BIR avantajı da bir XML belgesinin uygunlubir korunabilmesidir. Veri **kümesi** , **READXML**kullanılarak bir XML belgesinden doldurulursa, VERILER **WriteXml** kullanılarak bir XML BELGESI olarak geri yazıldığında, özgün XML belgesinden önemli ölçüde farklı olabilir. Bunun nedeni, **veri kümesinin** boşluk gibi BIÇIMLENDIRMELERI veya XML belgesinden öğe sırası gibi hiyerarşik bilgileri korumadığından kaynaklanır. **Veri kümesi** , **veri kümesinin**ŞEMASıYLA eşleşmediği için yoksayılan XML belgesinden öğeleri içermez. Bir **XmlDataDocument** Ile bir **veri** KÜMESIYLE eşitleme, özgün XML belgesinin biçimlendirme ve hiyerarşik öğe yapısının **XmlDataDocument**'Te tutulmasını sağlar, ancak veri **kümesi** yalnızca verileri içerir ve **veri kümesine**uygun şema bilgileri.  
  
 Bir **veri kümesini** **XmlDataDocument**ile eşitlerken sonuçlar, nesnelerinizin <xref:System.Data.DataRelation> iç içe yerleştirilmiş olmasına bağlı olarak farklılık gösterebilir. Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DataSet’i bir XmlDataDocument ile Eşitleme](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 Türü kesin belirlenmiş bir **veri kümesinin**, en az şemayla, **XmlDataDocument**ile eşitlenmesi gösterilmektedir.  
  
 [DataSet Üzerinde XPath Sorgusu Gerçekleştirme](performing-an-xpath-query-on-a-dataset.md)  
 Bir **veri kümesinin**içeriğinde XPath sorgusu gerçekleştirmeyi gösterir.  
  
 [DataSet’e XSLT Dönüşümü Uygulama](applying-an-xslt-transform-to-a-dataset.md)  
 Bir **veri kümesinin**içeriğine XSLT dönüşümü uygulamayı gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [DataSet içinde XML kullanma](using-xml-in-a-dataset.md)  
 Veri kümesinin, XML verileri olarak bir veri **kümesinin** içeriğini yükleme ve kalıcı hale getirme da dahil olmak üzere XML ile XML ile nasıl etkileşime gireceğini açıklar.  
  
 [DataRelations’ı İç İçe Yerleştirme](nesting-datarelations.md)  
 Bir **veri kümesinin** içeriğini XML verisi olarak temsil eden Iç içe **DataRelation** nesnelerinin önemini açıklar ve bu ilişkilerin nasıl oluşturulacağını açıklar.  
  
 [DataSets, DataTables ve DataViews](index.md)  
 Veri **kümesini** ve uygulama verilerini yönetmek ve ilişkisel VERITABANLARı ile XML dahil veri kaynaklarıyla etkileşim kurmak için kullanmayı açıklar.  
  
 <xref:System.Xml.XmlDataDocument>  
 **XmlDataDocument** sınıfı hakkında başvuru bilgileri içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
