---
title: Geçerli içerik XElement ve XDocument Objects3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 32521941bacdf8d689a81f6136d427307481ddc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Geçerli içerik XElement ve XDocument nesneleri
Bu konuda oluşturucular ve içerik öğelerini ve belgeleri eklemek için kullandığınız yöntemleri için geçirilen geçerli bağımsız değişkenler açıklanmaktadır.  
  
## <a name="valid-content"></a>Geçerli içerik  
 Sorguları genellikle değerlendirmek için <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XAttribute>. Koleksiyonları geçirebilir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri <xref:System.Xml.Linq.XElement> Oluşturucusu. Bu nedenle, bir sorgunun sonuçlarını içeriği olarak yöntemlere ve XML ağaçları doldurmak için kullandığınız oluşturucular geçirmek uygundur.  
  
 Basit içerik eklerken, çeşitli türleri bu yönteme geçirilen. Geçerli türler şunlardır:  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   Uygulayan herhangi bir türü `Object.ToString`.  
  
-   Uygulayan herhangi bir türü <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Karmaşık içerik eklerken, çeşitli türleri bu yönteme geçirilen:  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   Uygulayan herhangi bir türü <xref:System.Collections.Generic.IEnumerable%601>  
  
 Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>nesne koleksiyonunda numaralandırılan ve koleksiyondaki tüm öğeleri eklenir. Koleksiyon içeriyorsa <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneleri, koleksiyondaki her öğe ayrı olarak eklenir. Koleksiyon metin (ya da metne dönüştürülecek nesneleri) içeriyorsa, koleksiyon metinde birleştirilmiş ve tek bir metin düğümü olarak eklenir.  
  
 İçerik `null`, hiçbir şey eklenir. Ne zaman bir koleksiyon öğelerini koleksiyonda geçirme olabilir `null`. A `null` öğesi koleksiyonu ağaç üzerinde hiçbir etkisi olmaz.  
  
 Eklenen bir öznitelik içeren öğe içinde benzersiz bir ad olmalıdır.  
  
 Eklerken <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içeriğe üst öğeye sahipse, ardından nesneleri yalnızca bağlı XML ağacına. Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, ardından yeni içerik kopyalanabilen ve yeni kopyalanmış içerik XML ağacına eklenir.  
  
## <a name="valid-content-for-documents"></a>Belgeler için geçerli içerik  
 Öznitelikler ve basit içerik belgeye eklenemez.  
  
 Oluşturmak gereken birçok senaryo olmayan bir <xref:System.Xml.Linq.XDocument>. Bunun yerine, XML ağaçlar olan genellikle oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> kök düğümü. Sürece bir belge (örneğin, işleme yönergeleri ve açıklamalar en üst düzeyinde oluşturmak zorunda veya belge türlerini desteklemek zorunda olduğundan) oluşturmak için belirli bir gereksinim vardır, genellikle daha yararlıdır kullanmak uygun <xref:System.Xml.Linq.XElement> kök düğümü.  
  
 Bir belge için geçerli içerik aşağıdakileri içerir:  
  
-   Sıfır veya bir <xref:System.Xml.Linq.XDocumentType> nesneleri. Belge türü öğeden önce gelmelidir.  
  
-   Sıfır veya bir öğe.  
  
-   Sıfır veya daha fazla açıklama.  
  
-   Sıfır veya daha fazla işleme yönergeler.  
  
-   Yalnızca sıfır veya daha fazla metin düğümleri boşluk.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Oluşturucular ve içerik eklemeye izin ver işlevleri  
 Aşağıdaki yöntemlerden alt içeriği eklemenize izin bir <xref:System.Xml.Linq.XElement> veya bir <xref:System.Xml.Linq.XDocument>:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Oluşturan bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Oluşturan bir <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Alt öğe içeriğini sonuna ekler <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Sonra içerik ekler <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Önce içeriği ekler <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Alt öğe içeriğini başında içeriği ekler <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Tüm içeriği (alt düğümleri ve öznitelikleri) değiştiren bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Özniteliklerini değiştirir bir <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Alt düğümler ile yeni içerik değiştirir.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Bir düğüm yeni içerikle değiştirir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
