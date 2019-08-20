---
title: XElement ve XDocument Objects3 'ın geçerli Içeriği
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590940"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>XElement ve XDocument Nesnelerinin Geçerli İçeriği
Bu konuda, öğelere ve belgelere içerik eklemek için kullandığınız oluşturuculara ve yöntemlere geçirilebilecek geçerli bağımsız değişkenler açıklanmaktadır.  
  
## <a name="valid-content"></a>Geçerli Içerik  
 <xref:System.Collections.Generic.IEnumerable%601> Sorgular genellikle <xref:System.Xml.Linq.XElement> veya <xref:System.Collections.Generic.IEnumerable%601> '<xref:System.Xml.Linq.XAttribute>nin sonucunu vermez. <xref:System.Xml.Linq.XElement> Veya<xref:System.Xml.Linq.XAttribute> nesne<xref:System.Xml.Linq.XElement> koleksiyonlarını oluşturucuya geçirebilirsiniz. Bu nedenle, bir sorgunun sonuçlarını, XML ağaçlarını doldurmak için kullandığınız yöntemlere ve oluşturuculara içerik olarak geçirmek kullanışlı olur.  
  
 Basit içerik eklerken bu yönteme çeşitli türler geçirilebilir. Geçerli türler şunlardır:  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- Uygulayan `Object.ToString`herhangi bir tür.  
  
- Uygulayan <xref:System.Collections.Generic.IEnumerable%601>herhangi bir tür.  
  
 Karmaşık içerik eklerken bu yönteme çeşitli türler geçirilebilir:  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Uygulayan herhangi bir tür<xref:System.Collections.Generic.IEnumerable%601>  
  
 Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601>, nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir. Koleksiyon veya <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir. Koleksiyon metin içeriyorsa (veya metne dönüştürülen nesneler), koleksiyondaki metin birleştirilir ve tek bir metin düğümü olarak eklenir.  
  
 İçerik `null`varsa, hiçbir şey eklenmez. Koleksiyonda bir koleksiyon öğelerini geçirirken olabilir `null`. Koleksiyondaki `null` bir öğenin ağacı üzerinde hiçbir etkisi yoktur.  
  
 Eklenen bir öznitelik, kapsayan öğesi içinde benzersiz bir ada sahip olmalıdır.  
  
 <xref:System.Xml.Linq.XNode> Veya<xref:System.Xml.Linq.XAttribute> nesneleri eklerken, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir. Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.  
  
## <a name="valid-content-for-documents"></a>Belgeler için geçerli Içerik  
 Öznitelikler ve basit içerik belgeye eklenemez.  
  
 Oluşturmanız gereken pek çok senaryo yoktur <xref:System.Xml.Linq.XDocument>. Bunun yerine, genellikle bir <xref:System.Xml.Linq.XElement> kök düğümü olan XML ağaçlarınızı oluşturabilirsiniz. Bir belge oluşturmak için özel bir gereksinime sahip değilseniz (örneğin, en üst düzeyde işlem yönergeleri ve açıklamalar oluşturmanız veya belge türlerini desteklemeniz gerektiğinden), genellikle kök düğümünüz olarak kullanılması <xref:System.Xml.Linq.XElement> daha uygundur.  
  
 Bir belge için geçerli içerik şunları içerir:  
  
- Sıfır veya bir <xref:System.Xml.Linq.XDocumentType> nesne. Belge türlerinin öğeden önce gelmesi gerekir.  
  
- Sıfır veya bir öğe.  
  
- Sıfır veya daha fazla açıklama.  
  
- Sıfır veya daha fazla işleme yönergesi.  
  
- Yalnızca boşluk içeren sıfır veya daha fazla metin düğümü.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Içerik eklemeye Izin veren oluşturucular ve Işlevler  
 Aşağıdaki yöntemler bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>veya öğesine alt içerik eklemenize olanak tanır:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<xref:System.Xml.Linq.XElement>Oluşturur.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Bir <xref:System.Xml.Linq.XDocument>oluşturur.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<xref:System.Xml.Linq.XElement> Veya<xref:System.Xml.Linq.XDocument>alt içeriğinin sonuna ekler.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Öğesinden sonra <xref:System.Xml.Linq.XNode>içerik ekler.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Öğesinden önce <xref:System.Xml.Linq.XNode>içerik ekler.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Öğesinin alt içeriğinin başlangıcına içerik ekler <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Bir <xref:System.Xml.Linq.XElement>öğesinin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|İçindeki özniteliklerini <xref:System.Xml.Linq.XElement>değiştirir.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Alt düğümleri yeni içerikle değiştirir.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Bir düğümü yeni içerikle değiştirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları oluşturma (C#)](./linq-to-xml-overview.md)
