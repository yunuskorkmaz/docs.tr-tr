---
title: Serileştirilirken boşluğu koru-LINQ to XML
description: Bir XML ağacını serileştirmede çeşitli yollarla boşluk denetimi yapabilirsiniz.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553075"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a>Serileştirilirken boşluğu koru (LINQ to XML)

Bu makalede, bir XML ağacı serileştirilirken beyaz boşluğun nasıl denetleneceği açıklanır.

Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (yani, beyaz boşluğu korumadan), XML üzerinde bazı işlemler yapın ve ardından XML 'i girintilemeli olarak kaydeder. XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur. Bu, LINQ to XML için varsayılan davranıştır.

Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir. Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz. Bunu LINQ to XML yapmak için, XML 'yi yüklerken veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyabilirsiniz.

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>XML ağaçlarını seri hale getirme yöntemlerinin beyaz boşluk davranışı

<xref:System.Xml.Linq.XElement>Ve sınıflarında aşağıdaki yöntemler <xref:System.Xml.Linq.XDocument> bir xml ağacını serileştirin. Bir XML ağacını bir dosyaya, a 'ya veya bir dosyasına seri hale getirebilirsiniz <xref:System.IO.TextReader> <xref:System.Xml.XmlReader> . `ToString`Yöntemi bir dizeye seri hale getirir.

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [XElement. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [XDocument. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

Yöntem <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak ele yaramazsa, yöntemi SERILEŞTIRILMIŞ XML 'i biçimlendirir (girintili). Bu durumda, XML ağacındaki tüm önemli boşluklar atılır.

Yöntemi <xref:System.Xml.Linq.SaveOptions> bir bağımsız değişken olarak ele alıyorsa, yöntemin SERILEŞTIRILMIŞ XML 'yi biçimlendirme (girintileme) seçeneğini belirtebilirsiniz. Bu durumda, XML ağacındaki tüm boşluklar korunur.
