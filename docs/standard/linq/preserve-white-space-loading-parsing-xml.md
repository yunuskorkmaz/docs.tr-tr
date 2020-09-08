---
title: XML 'yi yüklerken veya ayrıştırırken boşluğu koru-LINQ to XML
description: XML ağaçlarını dolduran LINQ to XML yöntemlerinin boşluk davranışını kontrol edebilirsiniz. Örneğin, bellek içi işleme için Girintiyi kaldırabilir veya olduğu gibi bırakabilirsiniz.
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 783a1198f0b1754c690f04159860056a0fbadeb4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553094"
---
# <a name="preserve-white-space-while-loading-or-parsing-xml-linq-to-xml"></a>XML 'yi yüklerken veya ayrıştırırken boşluğu koru (LINQ to XML)

Bu makalede LINQ to XML boşluk davranışının nasıl denetleneceği açıklanır.

Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (yani, beyaz boşluğu korumadan), XML üzerinde bazı işlemler yapın ve ardından XML 'i girintilemeli olarak kaydeder. XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur. Bu, LINQ to XML için varsayılan davranıştır.

Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir. Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz. Bunu LINQ to XML yapmak için, XML 'yi yüklerken veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyabilirsiniz.

Bu makalede, XML ağaçlarının Doldurulmakta olduğu yöntemlerin boşluk davranışı açıklanır. XML ağaçlarını seri hale getirirken boşluk denetleme hakkında daha fazla bilgi için bkz. [serileştirilirken boşluk koruma](preserve-white-space-serializing.md).

## <a name="behavior-of-methods-that-populate-xml-trees"></a>XML ağaçlarını dolduran yöntemlerin davranışı

<xref:System.Xml.Linq.XElement>Ve sınıflarında aşağıdaki yöntemler <xref:System.Xml.Linq.XDocument> bir xml ağacını dolduracaktır. Bir dosya, bir <xref:System.IO.TextReader> , bir veya bir dizeden BIR XML ağacını doldurabilirsiniz <xref:System.Xml.XmlReader> :

- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>

Yöntem <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak ele yaramazsa Yöntem, önemli olmayan boşlukları korumaz.

Çoğu durumda, yöntemi <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak alırsa, isteğe bağlı boşluğu XML ağacında metin düğümleri olarak koruyabilirsiniz. Ancak, yöntemi bir öğesinden XML 'yi yüklüyorsanız, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader> boşluk olup olmayacağını belirler. Ayarın <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> hiçbir etkisi olmayacaktır.

Bu yöntemlerle, boşluk korununca, düğüm olarak XML ağacına önemli bir boşluk eklenir <xref:System.Xml.Linq.XText> . Boşluk korunmazsa, metin düğümleri eklenmez.

Kullanarak bir XML ağacı oluşturabilirsiniz <xref:System.Xml.XmlWriter> . Öğesine yazılan düğümler <xref:System.Xml.XmlWriter> ağaçta doldurulur. Ancak, bu yöntemi kullanarak bir XML ağacı oluşturduğunuzda, düğümün boşluk olup olmamasına veya boşluk olmasına bakılmaksızın tüm düğümler korunur.
