---
title: Var olan düğümleri bir belgeden diğerine kopyalama
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 744c97e8728d0a65bff8e7bb7a7dbb298afe1800
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036375"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Var olan düğümleri bir belgeden diğerine kopyalama
**ImportNode** yöntemi tarafından bir düğüm veya tüm düğüm alt ağacı kopyalandığı birinden mekanizmasıdır **XmlDocument** diğerine. Çağrısından döndürülen düğümü öznitelik değerleri, düğüm adı, düğüm türü ve ön ek, yerel ad ve ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) gibi tüm ad alanı ile ilgili özniteliklere de dahil olmak üzere kaynak belge düğümünden bir kopyasıdır. Kaynak belge değiştirilmez. Düğüm içe aktardıktan sonra hala düğümleri eklemek için kullanılan yöntemlerden birini kullanarak ağacına eklemeniz gerekir.  
  
 Düğüm, yeni bir belgeye eklendiğinde, yeni belgeyi bir düğümün sahip olduğu. Düğümlerden ayrı bir belge parçalarını oluşturulmamış olsa bile her düğüm oluşturulduğunda, sahip olan bir belge olduğunu nedenidir. Bu XML belge nesne modeli (DOM) bir gereksinimdir ve Fabrika oluşturma tasarım gereği zorunlu kılınır **XmlDocument** sınıfı. Örneğin, **CreateElement**, yeni bir düğüm oluşturmak için tek yoludur.  
  
 İçeri aktarılan düğüme ve değerini düğüm türüne bağlı olarak *derin* parametresi, ek bilgi uygun şekilde kopyalanır. Bir XML parçası, Beklenen davranış yansıtmak üzere bu yöntem çalışır veya HTML kaynağını bir belgeden diğerine XML için farklı bir belge türü tanımları (DTD'ler) iki belge olabilir olgusu için hesap kopyalanmıştır.  
  
 Belirli bir davranışı aktarılabilen düğüm türlerinin her biri için aşağıdaki tabloda açıklanmaktadır.  
  
|Düğüm türü|*ayrıntılı* parametre değeri true|*ayrıntılı* parametre yanlış|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> Ayarlanır **true** XmlAttribute üzerinde. Kaynak alt öğeleri **XmlAttribute** karşılık gelen alt ağacı oluşturmak için yinelemeli olarak içeri aktarıldı ve sonuçta elde edilen düğümlerin yeniden.|*Derin* parametresi için geçerli değildir **XmlAttribute** düğümler, çünkü bunlar her zaman kendi alt düğümler ile bunları içeri aktarıldığında Yürüt.|  
|XmlCDataSection|Verileri dahil olmak üzere düğümü kopyalar.|Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlComment|Verileri dahil olmak üzere düğümü kopyalar.|Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlDocumentFragment|Alt kaynak düğümünün yinelemeli olarak içeri aktarıldı ve karşılık gelen alt ağacı oluşturmak için yeniden elde edilen düğümler var.|Boş bir **XmlDocumentFragment** oluşturulur.|  
|XmlDocumentType|Düğümü kendi verisini dahil olmak üzere, kopyalar.|Düğümü kendi verisini dahil olmak üzere, kopyalar.|  
|XmlElement|Kaynak öğesi alt öğeleri yinelemeli olarak içeri aktarıldı ve karşılık gelen alt ağacı oluşturmak için yeniden elde edilen düğümler var. **Not:** varsayılan öznitelik kopyalanmaz. İçeri aktarılan belge bu öğe adı için varsayılan öznitelikler tanımlıyorsa, bunlar atanır.|Belirtilen öznitelik düğümleri kaynak öğenin alınır ve oluşturulan **XmlAttribute** düğümleri, yeni bir öğe için eklenir. Alt düğümler kopyalanmaz. **Not:** varsayılan öznitelik kopyalanmaz. İçeri aktarılan belge bu öğe adı için varsayılan öznitelikler tanımlıyorsa, bunlar atanır.|  
|XmlEntityReference|Kaynak ve hedef belgeleri farklı şekilde tanımlanmış varlıkların sahip olabileceğinden, bu yöntem yalnızca kopyalar **XmlEntityReference** düğümü. Yerine konacak metin dahil değildir. Hedef belgede tanımlanan varlığı varsa, değeri atanır.|Kaynak ve hedef belgeleri farklı şekilde tanımlanmış varlıkların sahip olabileceğinden, bu yöntem yalnızca kopyalar **XmlEntityReference** düğümü. Yerine konacak metin dahil değildir. Hedef belgede tanımlanan varlığı varsa, değeri atanır.|  
|XmlProcessingInstruction|Hedef ve veri değeri, içeri aktarılan bir düğümden diğerine kopyalar.|Hedef ve veri değeri, içeri aktarılan bir düğümden diğerine kopyalar.|  
|XmlText|Verileri dahil olmak üzere düğümü kopyalar.|Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlSignificantWhitespace|Verileri dahil olmak üzere düğümü kopyalar.|Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlWhitespace|Verileri dahil olmak üzere düğümü kopyalar.|Verileri dahil olmak üzere düğümü kopyalar.|  
|XmlDeclaration|Hedef ve veri değeri, içeri aktarılan bir düğümden diğerine kopyalar.|Hedef ve veri değeri, içeri aktarılan bir düğümden diğerine kopyalar.|  
|Diğer tüm düğüm türleri|Bu düğüm türü içeri aktarılamıyor.|Bu düğüm türü içeri aktarılamıyor.|  
  
> [!NOTE]
>  DocumentType düğümleri aktarılabilen olsa da, bir belgeyi yalnızca bir DocumentType olabilir. Bu nedenle, belge türü emin olmak için sahip olduğunuz ağacına eklemeden önce olarak içe aktardıktan sonra belge türü yok belge. Düğümleri kaldırma hakkında daha fazla bilgi için bkz: [düğümleri kaldırma, içerik ve değerleri XML belgesinden](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
