---
title: Varolan düğümleri bir belgeden kopyalama
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca36ffdd2eb5eb3acfbacbd543eebf17cfffb5d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573932"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Varolan düğümleri bir belgeden kopyalama
**ImportNode** yöntemi olarak bir düğüm veya tüm düğüm alt ağacı kopyalanır birinden mekanizmasıdır **XmlDocument** başka bir. Çağrısından döndürülen düğümü, öznitelik değerleri, düğüm adı, düğüm türü ve tüm ad alanı ilgili öznitelikleri öneki, yerel ad ve ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) gibi dahil olmak üzere kaynak belge düğümden kopyasıdır. Kaynak belge değiştirilmez. Düğüm içe aktardıktan sonra hala düğümleri eklemek için kullanılan yöntemlerden birini kullanarak ağacına eklemeniz gerekir.  
  
 Düğümü yeni belgeye eklendiğinde, yeni belge düğümü sahip olur. Düğümleri ayrı belge parçalanma oluşturulmamış olsa bile oluşturduğunuzda, her düğümün sahip olan bir belgeyi sahip nedenidir. Bu gereksinim XML belge nesne modeli (DOM) ve Fabrika oluşturma tasarım gereği uygulanır **XmlDocument** sınıfı. Örneğin, **CreateElement**, yeni bir düğüm oluşturmak için tek yoludur.  
  
 İçeri aktarılan düğümü ve değeri düğüm türüne bağlı olarak *derin* parametresi, ek bilgi uygun şekilde kopyalanır. XML parçasında, beklenen davranışı yansıtmak üzere bu yöntemi çalışır ya da HTML kaynağını XML için farklı bir belge türü tanımları (DTD) iki belge olabilir olgu için hesap başka bir bir belgeden kopyalanan.  
  
 Aşağıdaki tabloda her alınabilir düğüm türü için belirli bir davranışı açıklar.  
  
|Düğüm türü|*derin* parametre değeri true|*derin* parametre yanlış|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> Ayarlanır **true** XmlAttribute üzerinde. Kaynak alt öğeleri **XmlAttribute** karşılık gelen alt ağacı oluşturmak için yeniden içeri yinelemeli ve sonuçta elde edilen düğüm.|*Derin* parametresi için geçerli olmayan **XmlAttribute** düğümleri, bunlar her zaman kendi alt düğümleri onlarla aktarıldığında taşımak için.|  
|XmlCDataSection|Verileri de dahil olmak üzere düğümü kopyalar.|Verileri de dahil olmak üzere düğümü kopyalar.|  
|XmlComment|Verileri de dahil olmak üzere düğümü kopyalar.|Verileri de dahil olmak üzere düğümü kopyalar.|  
|XmlDocumentFragment|Kaynak düğüm alt öğeleri içe yinelemeli ve karşılık gelen alt ağacı oluşturmak için yeniden elde edilen düğümler var.|Boş bir **XmlDocumentFragment** oluşturulur.|  
|XmlDocumentType|Kendi verisini dahil olmak üzere düğümü kopyalar.|Kendi verisini dahil olmak üzere düğümü kopyalar.|  
|XmlElement|Kaynak öğenin alt öğeleri içe yinelemeli ve karşılık gelen alt ağacı oluşturmak için yeniden elde edilen düğümler var. **Not:** varsayılan öznitelikleri kopyalanmadı. İçeri aktarılan belge bu öğe adı için varsayılan özniteliklerini tanımlıyorsa, bu atanır.|Belirtilen öznitelik kaynak öğesinin düğümleri alınır ve oluşturulan **XmlAttribute** düğümleri yeni öğesine eklenir. Alt düğümler kopyalanmaz. **Not:** varsayılan öznitelikleri kopyalanmadı. İçeri aktarılan belge bu öğe adı için varsayılan özniteliklerini tanımlıyorsa, bu atanır.|  
|XmlEntityReference|Kaynak ve hedef belgeler farklı tanımlanan varlıklar olabilir çünkü bu yöntem yalnızca kopyalar **XmlEntityReference** düğümü. Değiştirme metnini dahil değildir. Hedef belgede tanımlanan varlık varsa, değeri atanır.|Kaynak ve hedef belgeler farklı tanımlanan varlıklar olabilir çünkü bu yöntem yalnızca kopyalar **XmlEntityReference** düğümü. Değiştirme metnini dahil değildir. Hedef belgede tanımlanan varlık varsa, değeri atanır.|  
|XmlProcessingInstruction|Hedef ve veriyi değeri içeri aktarılan düğümden kopyalar.|Hedef ve veriyi değeri içeri aktarılan düğümden kopyalar.|  
|XmlText|Verileri de dahil olmak üzere düğümü kopyalar.|Verileri de dahil olmak üzere düğümü kopyalar.|  
|XmlSignificantWhitespace|Verileri de dahil olmak üzere düğümü kopyalar.|Verileri de dahil olmak üzere düğümü kopyalar.|  
|XmlWhitespace|Verileri de dahil olmak üzere düğümü kopyalar.|Verileri de dahil olmak üzere düğümü kopyalar.|  
|XmlDeclaration|Hedef ve veriyi değeri içeri aktarılan düğümden kopyalar.|Hedef ve veriyi değeri içeri aktarılan düğümden kopyalar.|  
|Diğer tüm düğüm türleri|Bu düğüm türleri aktarılamaz.|Bu düğüm türleri aktarılamaz.|  
  
> [!NOTE]
>  DocumentType düğümleri alınabilir karşın, bir belgeyi yalnızca bir DocumentType olabilir. Bu nedenle, emin olmak için sahip ağacına eklemeden önce belge türü içe aktardıktan sonra belge türü yok belgede. Düğümleri kaldırma hakkında daha fazla bilgi için bkz: [düğümleri kaldırma, içerik ve bir XML belgesi değerlerinden](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
