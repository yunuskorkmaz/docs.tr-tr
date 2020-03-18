---
title: XElement ve XDocument Nesneleringeçerli İçeriği3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590940"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>XElement ve XDocument Nesnelerinin Geçerli İçeriği
Bu konu, öğelere ve belgelere içerik eklemek için kullandığınız oluşturuculara ve yöntemlere geçirilebilen geçerli bağımsız değişkenleri açıklar.  
  
## <a name="valid-content"></a>Geçerli İçerik  
 Sorgular <xref:System.Collections.Generic.IEnumerable%601> genellikle <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute>'nin veya Koleksiyonlarını veya <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> nesnelerini <xref:System.Xml.Linq.XElement> oluşturucuya geçirebilirsiniz. Bu nedenle, xml ağaçları doldurmak için kullandığınız yöntemler ve yapıcılar içine içerik olarak bir sorgu sonuçlarını geçmek için uygundur.  
  
 Basit içerik eklerken, bu yönteme çeşitli türler de aktarılabilir. Geçerli türleri şunlardır:  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- Uygulayan herhangi bir `Object.ToString`tür.  
  
- Uygulayan herhangi bir <xref:System.Collections.Generic.IEnumerable%601>tür.  
  
 Karmaşık içerik eklerken, çeşitli türler bu yönteme geçirilebilir:  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Uygulayan herhangi bir tür<xref:System.Collections.Generic.IEnumerable%601>  
  
 Bir nesne uygularsa, <xref:System.Collections.Generic.IEnumerable%601>nesnedeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir. Koleksiyon <xref:System.Xml.Linq.XNode> içeriyorsa <xref:System.Xml.Linq.XAttribute> veya nesnelere, koleksiyondaki her öğe ayrı olarak eklenir. Koleksiyon metin (veya metne dönüştürülen nesneler) içeriyorsa, koleksiyondaki metin birleştirilmiş ve tek bir metin düğümü olarak eklenir.  
  
 İçerik ise, `null`hiçbir şey eklenmez. Koleksiyondaki bir koleksiyon öğesi geçerken `null`. Koleksiyondaki bir `null` öğenin ağaç üzerinde hiçbir etkisi yoktur.  
  
 Eklenen bir öznitelik, içerdiği öğe içinde benzersiz bir ada sahip olmalıdır.  
  
 Eklerken <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute> veya nesneler eklerken, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir. Yeni içerik zaten ebeveynliyse ve başka bir XML ağacının parçasıysa, yeni içerik klonlanır ve yeni klonlanan içerik XML ağacına eklenir.  
  
## <a name="valid-content-for-documents"></a>Belgeler için Geçerli İçerik  
 Bir belgeye öznitelikler ve basit içerik eklenemez.  
  
 Bir <xref:System.Xml.Linq.XDocument>tane oluşturmanızı gerektiren çok fazla senaryo yoktur. Bunun yerine, genellikle <xref:System.Xml.Linq.XElement> bir kök düğümü ile XML ağaçları oluşturabilirsiniz. Belge oluşturmak için belirli bir gereksiniminiz yoksa (örneğin, en üst düzeyde işleme yönergeleri ve açıklamaları oluşturmanız veya belge türlerini <xref:System.Xml.Linq.XElement> desteklemeniz gerekmediği için), kök düğümünüz olarak kullanmak genellikle daha uygundur.  
  
 Bir belge için geçerli içerik aşağıdakileri içerir:  
  
- Sıfır veya <xref:System.Xml.Linq.XDocumentType> bir nesne. Belge türleri öğeden önce gelmelidir.  
  
- Sıfır veya bir öğe.  
  
- Sıfır veya daha fazla yorum.  
  
- Sıfır veya daha fazla işlem talimatı.  
  
- Yalnızca beyaz boşluk içeren sıfır veya daha fazla metin düğümü.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>İçerik Eklemeye İzin Veren Yapıcılar ve İşlevler  
 Aşağıdaki yöntemler, bir veya bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>alt içerik eklemek için izin verir:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Bir <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Or'un alt içeriğinin <xref:System.Xml.Linq.XElement> sonuna <xref:System.Xml.Linq.XDocument>ekler.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Sonra içerik <xref:System.Xml.Linq.XNode>ekler.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Önce içerik <xref:System.Xml.Linq.XNode>ekler.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Alt içeriğin başında içerik <xref:System.Xml.Linq.XContainer>ekler.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Bir <xref:System.Xml.Linq.XElement>'nin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Bir <xref:System.Xml.Linq.XElement>' nin özniteliklerini değiştirir.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Çocuk düğümlerini yeni içerikle değiştirir.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Düğümü yeni içerikle değiştirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Ağaçları Oluşturma (C#)](./linq-to-xml-overview.md)
