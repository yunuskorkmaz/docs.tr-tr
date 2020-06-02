---
title: Var Olan Düğümleri Bir Belgeden Diğerine Kopyalama
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
ms.openlocfilehash: 8ae7fd04e5c85e59ca9bd629c6957ad470d36b48
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289206"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Var Olan Düğümleri Bir Belgeden Diğerine Kopyalama
**ImportNode** yöntemi, bir düğümün veya tüm düğüm alt ağacının bir **XmlDocument** 'dan diğerine kopyalandığı mekanizmadır. Çağrıdan döndürülen düğüm, öznitelik değerleri, düğüm adı, düğüm türü ve önek, yerel ad ve ad alanı Tekdüzen Kaynak tanımlayıcısı (URI) gibi tüm ad alanıyla ilgili öznitelikleri dahil olmak üzere kaynak belgesinden düğümün bir kopyasıdır. Kaynak belge değiştirilmez. Düğümü içeri aktardıktan sonra, düğümleri eklemek için kullanılan yöntemlerden birini kullanarak ağaca yine de eklemeniz gerekir.  
  
 Düğüm yeni belgeye eklendiğinde, yeni belge düğümün sahibi olur. Bunun nedeni, oluşturulan her düğümün, düğümler ayrı belge parçalarında oluşturulsa bile, sahip olduğu bir belgeye sahip olması nedenidir. Bu, XML Belge Nesne Modeli (DOM) gereksinimidir ve **XmlDocument** sınıfında fabrika oluşturma tasarımı tarafından zorlanır. Örneğin, **CreateElement**, yeni düğümler oluşturmanın tek yoludur.  
  
 İçeri aktarılan düğümün düğüm türüne ve *derin* parametresinin değerine bağlı olarak, ek bilgiler uygun şekilde kopyalanır. Bu yöntem, XML veya HTML kaynağının bir parçası bir belgeden diğerine kopyalanırsa, XML için iki belgede farklı belge türü tanımlarına (DTD 'Ler) sahip olabileceği için beklenen davranışı yansıtmaya çalışır.  
  
 Aşağıdaki tabloda, içeri aktarılabilecek her düğüm türü için belirli davranış açıklanmaktadır.  
  
|Düğüm türü|*derin* parametre doğru|*derin* parametre yanlış|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|, <xref:System.Xml.XmlAttribute.Specified%2A> XmlAttribute üzerinde **true** olarak ayarlanır. Kaynak **XmlAttribute** 'in alt öğeleri yinelemeli olarak içeri aktarılır ve elde edilen düğümler, karşılık gelen alt ağacı oluşturmak için yeniden birleştirir.|*Derin* parametresi, her zaman içeri aktarıldığında her zaman alt düğümlerini taşıdıklarından, **XmlAttribute** düğümleri için uygulanmaz.|  
|XmlCDataSection|, Verileri dahil olmak üzere düğümü kopyalar.|, Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlComment|, Verileri dahil olmak üzere düğümü kopyalar.|, Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlDocumentFragment|Kaynak düğümün alt öğeleri yinelemeli olarak içeri aktarılır ve elde edilen düğümler, karşılık gelen alt ağacı oluşturmak için yeniden birleştirir.|Boş bir **XmlDocumentFragment** oluşturulur.|  
|XmlDocumentType|, Verileri dahil olmak üzere düğümü kopyalar. *|, Verileri dahil olmak üzere düğümü kopyalar. *|  
|XmlElement|Kaynak öğenin alt öğeleri yinelemeli olarak içeri aktarılır ve elde edilen düğümler, karşılık gelen alt ağacı oluşturmak için yeniden birleştirir. **Note:**  Varsayılan öznitelikler kopyalanmaz. İçeri aktarılan belge, bu öğe adı için varsayılan öznitelikleri tanımlıyorsa, bunlar atanır.|Kaynak öğenin belirtilen öznitelik düğümleri içeri aktarılır ve oluşturulan **XmlAttribute** düğümleri yeni öğeye eklenir. Alt düğümler kopyalanmaz. **Note:**  Varsayılan öznitelikler kopyalanmaz. İçeri aktarılan belge, bu öğe adı için varsayılan öznitelikleri tanımlıyorsa, bunlar atanır.|  
|XmlEntityReference|Kaynak ve hedef belgeler varlıkların farklı şekilde tanımlandığından, bu yöntem yalnızca **XmlEntityReference** düğümünü kopyalar. Değiştirme metni dahil değildir. Hedef belge tanımlı varlığa sahipse, değeri atanır.|Kaynak ve hedef belgeler varlıkların farklı şekilde tanımlandığından, bu yöntem yalnızca **XmlEntityReference** düğümünü kopyalar. Değiştirme metni dahil değildir. Hedef belge tanımlı varlığa sahipse, değeri atanır.|  
|Xmlprocessingyönergesi|İçeri aktarılan düğümden hedef ve veri değerini kopyalar.|İçeri aktarılan düğümden hedef ve veri değerini kopyalar.|  
|XmlText|, Verileri dahil olmak üzere düğümü kopyalar.|, Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlSignificantWhitespace|, Verileri dahil olmak üzere düğümü kopyalar.|, Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlWhitespace|, Verileri dahil olmak üzere düğümü kopyalar.|, Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlDeclaration|İçeri aktarılan düğümden hedef ve veri değerini kopyalar.|İçeri aktarılan düğümden hedef ve veri değerini kopyalar.|  
|Diğer tüm düğüm türleri|Bu düğüm türleri içeri aktarılamıyor.|Bu düğüm türleri içeri aktarılamıyor.|  
  
> [!NOTE]
> DocumentType düğümleri içeri aktarılabilse de bir belge yalnızca bir DocumentType içerebilir. Bu nedenle belge türünü içeri aktardıktan sonra, ağaca eklemeden önce belgede belge türü olmadığından emin olmanız gerekir. Düğümleri kaldırma hakkında bilgi için bkz. [BIR XML belgesinden düğümleri, içeriği ve değerleri kaldırma](removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
