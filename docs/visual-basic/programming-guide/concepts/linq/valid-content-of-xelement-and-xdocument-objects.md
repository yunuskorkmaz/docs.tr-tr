---
title: XElement ve XDocument Objects2 geçerli içerik
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: 5e9b5ec54b3005d18a1a0da10d78d3c8ad5300ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614358"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>XElement ve XDocument Nesnelerinin Geçerli İçeriği
Bu konuda, Oluşturucular ve öğelerini ve belgeleri için içerik eklemek için kullandığınız yöntemlere geçirilen geçerli bağımsız değişkenler açıklanmaktadır.  
  
## <a name="valid-content"></a>Geçerli içeriği  
 Sorgular genellikle değerlendirmek için <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XAttribute>. Koleksiyonları geçirebilirsiniz <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri için <xref:System.Xml.Linq.XElement> Oluşturucusu. Bu nedenle, yöntemleri ve XML ağaçlarını doldurmak için kullandığınız oluşturucular bir sorgunun sonuçlarını içeriği olarak geçirmek kullanışlıdır.  
  
 Basit içerik eklerken, çeşitli türleri bu yönteme geçirilebilir. Geçerli türleri aşağıdakileri kapsamaktadır:  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- Uygulayan herhangi bir tür `Object.ToString`.  
  
- Uygulayan herhangi bir tür <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Karmaşık içerik eklerken, çeşitli türleri bu yönteme geçirilen:  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Uygulayan herhangi bir tür <xref:System.Collections.Generic.IEnumerable%601>  
  
 Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>, koleksiyon nesnesi içinde listelenmiş ve koleksiyondaki tüm öğelerin eklenir. Koleksiyon içeriyorsa <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler, koleksiyondaki her öğe ayrı olarak eklenir. Koleksiyon, metin (veya metne dönüştürülür nesneleri) içeriyorsa, koleksiyondaki metin birleştirilmiş ve tek bir metin düğümü olarak eklendi.  
  
 İçerik `null`, hiçbir şey eklenir. Ne zaman bir koleksiyon, koleksiyondaki öğeleri geçirme olabilir `null`. A `null` öğesi koleksiyonu ağaç üzerinde hiçbir etkisi olmaz.  
  
 Eklenen bir öznitelik içeren öğe içinde benzersiz bir adı olmalıdır.  
  
 Eklerken <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içerik üstü yoksa, ardından nesneleri yalnızca bağlı XML ağacına. Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, ardından yeni içerik kopyalanmış olan ve yeni kopyalanan içeriği XML ağacına eklenir.  
  
## <a name="valid-content-for-documents"></a>Belgeler için geçerli içerik  
 Öznitelikler ve basit içerik belgeye eklenemiyor.  
  
 Oluşturmak ihtiyacınız olan birçok senaryo yok bir <xref:System.Xml.Linq.XDocument>. Bunun yerine, XML ağaçları genellikle oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> kök düğümü. Sürece belge (örneğin, işleme yönergeleri ve açıklamalar en üst düzeyinde oluşturmak zorunda veya belge türlerini desteklemek zorunda olduğundan) oluşturmak için belirli bir gereksiniminiz olmadığı, genellikle daha rahat kullanmak <xref:System.Xml.Linq.XElement> , kök düğümü olarak.  
  
 Bir belge için geçerli içerik aşağıdakileri içerir:  
  
- Sıfır veya bir <xref:System.Xml.Linq.XDocumentType> nesneleri. Belge türlerini öğeden önce gelmelidir.  
  
- Sıfır veya bir öğe.  
  
- Sıfır veya daha fazla açıklama.  
  
- Sıfır veya daha fazla işleme yönergeleri.  
  
- Yalnızca sıfır veya daha fazla metin düğümleri boşluk.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Oluşturucular ve içerik eklemeye izin ver işlevleri  
 Alt içeriğin eklemek aşağıdaki yöntemlerden izin bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Oluşturur bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Oluşturur bir <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Alt öğe içeriğini sonuna ekler <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Sonra içerik ekler <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Önce içeriği ekler <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|İçeriği, içerik alt başında ekler <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Tüm içeriğini (alt düğümleri ve öznitelikleri) yerini alan bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Özniteliklerini değiştirir bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Alt düğüm, yeni içerikle değiştirir.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Bir düğüm, yeni içerikle değiştirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
