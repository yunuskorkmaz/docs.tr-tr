---
title: XElement ve XDocument Objects3 'ın geçerli Içeriği
description: Öğelere ve belgelere içerik eklemek için kullandığınız oluşturuculara ve yöntemlere geçirilebileceğiniz geçerli bağımsız değişkenler hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302262"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>XElement ve XDocument Nesnelerinin Geçerli İçeriği
Bu konuda, öğelere ve belgelere içerik eklemek için kullandığınız oluşturuculara ve yöntemlere geçirilebilecek geçerli bağımsız değişkenler açıklanmaktadır.  
  
## <a name="valid-content"></a>Geçerli Içerik  
 Sorgular genellikle veya ' nin sonucunu vermez <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> . <xref:System.Xml.Linq.XElement>Veya <xref:System.Xml.Linq.XAttribute> nesne koleksiyonlarını oluşturucuya geçirebilirsiniz <xref:System.Xml.Linq.XElement> . Bu nedenle, bir sorgunun sonuçlarını, XML ağaçlarını doldurmak için kullandığınız yöntemlere ve oluşturuculara içerik olarak geçirmek kullanışlı olur.  
  
 Basit içerik eklerken bu yönteme çeşitli türler geçirilebilir. Geçerli türler şunlardır:  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- Uygulayan herhangi bir tür `Object.ToString` .  
  
- Uygulayan herhangi bir tür <xref:System.Collections.Generic.IEnumerable%601> .  
  
 Karmaşık içerik eklerken bu yönteme çeşitli türler geçirilebilir:  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Uygulayan herhangi bir tür<xref:System.Collections.Generic.IEnumerable%601>  
  
 Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601> , nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir. Koleksiyon <xref:System.Xml.Linq.XNode> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir. Koleksiyon metin içeriyorsa (veya metne dönüştürülen nesneler), koleksiyondaki metin birleştirilir ve tek bir metin düğümü olarak eklenir.  
  
 İçerik varsa `null` , hiçbir şey eklenmez. Koleksiyonda bir koleksiyon öğelerini geçirirken olabilir `null` . `null`Koleksiyondaki bir öğenin ağacı üzerinde hiçbir etkisi yoktur.  
  
 Eklenen bir öznitelik, kapsayan öğesi içinde benzersiz bir ada sahip olmalıdır.  
  
 <xref:System.Xml.Linq.XNode>Veya nesneleri eklerken <xref:System.Xml.Linq.XAttribute> , yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir. Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.  
  
## <a name="valid-content-for-documents"></a>Belgeler için geçerli Içerik  
 Öznitelikler ve basit içerik belgeye eklenemez.  
  
 Oluşturmanız gereken pek çok senaryo yoktur <xref:System.Xml.Linq.XDocument> . Bunun yerine, genellikle bir kök düğümü olan XML ağaçlarınızı oluşturabilirsiniz <xref:System.Xml.Linq.XElement> . Bir belge oluşturmak için özel bir gereksinime sahip değilseniz (örneğin, en üst düzeyde işlem yönergeleri ve açıklamalar oluşturmanız veya belge türlerini desteklemeniz gerektiğinden), genellikle <xref:System.Xml.Linq.XElement> kök düğümünüz olarak kullanılması daha uygundur.  
  
 Bir belge için geçerli içerik şunları içerir:  
  
- Sıfır veya bir <xref:System.Xml.Linq.XDocumentType> nesne. Belge türlerinin öğeden önce gelmesi gerekir.  
  
- Sıfır veya bir öğe.  
  
- Sıfır veya daha fazla açıklama.  
  
- Sıfır veya daha fazla işleme yönergesi.  
  
- Yalnızca boşluk içeren sıfır veya daha fazla metin düğümü.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Içerik eklemeye Izin veren oluşturucular ve Işlevler  
 Aşağıdaki yöntemler bir veya öğesine alt içerik eklemenize olanak tanır <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> :  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Oluşturur <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Bir oluşturur <xref:System.Xml.Linq.XDocument> .|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Veya alt içeriğinin sonuna ekler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> .|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Öğesinden sonra içerik ekler <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Öğesinden önce içerik ekler <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Öğesinin alt içeriğinin başlangıcına içerik ekler <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Bir öğesinin tüm içeriğini (alt düğümleri ve öznitelikleri) değiştirir <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|İçindeki özniteliklerini değiştirir <xref:System.Xml.Linq.XElement> .|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Alt düğümleri yeni içerikle değiştirir.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Bir düğümü yeni içerikle değiştirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları oluşturma (C#)](./linq-to-xml-overview.md)
