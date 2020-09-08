---
title: LINQ to XML ve diğer XML Teknolojileri
description: Daha iyi teknoloji seçimleri yapmak için LINQ to XML XSLT, MSXML ve XmlLite ile nasıl Karşılaştırıldığı hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: ac118543bd1101e50edfcf99a609a715b885bfbd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553478"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML ve diğer XML Teknolojileri

Bu makalede, LINQ to XML aşağıdaki XML teknolojileriyle karşılaştırılmaktadır: <xref:System.Xml.XmlReader> , XSLT, MSXML ve xmllite. Bu bilgiler hangi teknolojiden kullanacağınızı belirlemenize yardımcı olabilir.

Belge Nesne Modeli (DOM) LINQ to XML bir karşılaştırması için, bkz. [LINQ to XML vs. Dom](linq-xml-vs-dom.md).

## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML vs. XmlReader

<xref:System.Xml.XmlReader> hızlı, salt iletme, önbelleğe alınmamış bir ayrıştırıcıdır.

LINQ to XML, üzerine uygulanır <xref:System.Xml.XmlReader> ve sıkı bir şekilde tümleşiktir. Ancak doğrudan de kullanabilirsiniz <xref:System.Xml.XmlReader> .

Örneğin, saniyede yüzlerce XML belgesini ayrıştıracak bir Web hizmeti oluşturduğunuzu ve belgeler aynı yapıya sahip olduğundan, yalnızca XML 'i ayrıştırmak için kodun bir uygulamasını yazmanız gerekir. Bu durumda, muhtemelen doğrudan kullanmak isteyebilirsiniz <xref:System.Xml.XmlReader> .

Buna karşılık, çok küçük bir XML belgesi çözümleyen bir sistem oluşturuyorsanız ve her biri farklıysa, LINQ to XML sağladığı üretkenlik geliştirmelerinden yararlanmak isteyebilirsiniz.

## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML ile XSLT karşılaştırması

Hem LINQ to XML hem de XSLT, kapsamlı XML belge dönüştürme özellikleri sağlar. XSLT, kural tabanlı, bildirime dayalı bir yaklaşımdır. Gelişmiş XSLT programcıları, XSLT 'nin durum bilgisi olmayan bir yaklaşımı vurgulayarak işlevsel programlama stilinde yazar. Dönüşümler, yan etkileri olmadan uygulanan saf işlevleri kullanılarak yazılabilir. Bu kural tabanlı veya işlevsel yaklaşım birçok geliştiricilere tanıdık değildir ve öğrenmesi zor ve zaman alıcı olabilir.

XSLT, yüksek performanslı uygulamalar veren bir üretken sistem olabilir. Örneğin, bazı büyük Web şirketleri XSLT 'yi, farklı türde veri depolarından çekilen XML 'den HTML oluşturmak için bir yol olarak kullanır. Yönetilen XSLT altyapısı XSLT 'yi ortak dil çalışma zamanı (CLR) koduna derler ve bazı senaryolarda yerel XSLT altyapısından daha iyi performans sağlar.

Ancak XSLT, C# ' dan faydalanır ve birçok geliştiricinin sahip olduğu Visual Basic bilgi alabilir. Geliştiricilerin farklı ve karmaşık bir programlama dilinde kod yazmasını gerektirir. C# (veya Visual Basic) gibi tümleşik olmayan iki geliştirme sistemini ve XSLT 'nin geliştirilmesi ve bakımının daha zor olduğu yazılım sistemlerinde sonuç olarak kullanılması.

LINQ to XML sorgu ifadelerini ana oluşturduktan sonra, LINQ to XML dönüştürmeleri kullanımı kolay güçlü bir teknolojidir. Temel olarak, işlevsel oluşturma, çeşitli kaynaklardan veri çekme, <xref:System.Xml.Linq.XElement> nesneleri dinamik olarak oluşturma ve tümünü yeni BIR XML ağacına çevirme kullanarak XML belgenizi oluşturursunuz. Dönüştürme tamamen yeni bir belge oluşturabilir. LINQ to XML dönüşümler oluşturmak nispeten kolay ve sezgisel ve elde edilen kod okunabilir olur. Bu, geliştirme ve bakım maliyetlerini azaltır.

LINQ to XML XSLT 'yi değiştirmek için tasarlanmamıştır. XSLT, özellikle belgenin yapısı iyi tanımlanmamışsa, karmaşık ve belge merkezli XML dönüştürmeleri için seçim aracı olmaya devam etmektedir.

XSLT, World Wide Web Konsorsiyumu (W3C) standardı olmasının avantajına sahiptir. Yalnızca standartları olan teknolojileri kullandığınız bir gereksinime sahipseniz, XSLT daha uygun olabilir.

XSLT, XML 'dir ve bu nedenle program aracılığıyla işlenebilirler.

## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML vs. MSXML

MSXML, Microsoft Windows 'a dahil edilen XML 'yi işlemeye yönelik COM tabanlı teknolojisidir. MSXML, XPath ve XSLT desteğiyle DOM 'ın yerel bir uygulamasını sağlar. Ayrıca, SAX2 önbelleğe alınmamış olay tabanlı ayrıştırıcısı da içerir.

MSXML iyi çalışır, Çoğu senaryoda varsayılan olarak güvenlidir ve AJAX stili uygulamalarda istemci tarafı XML işlemesi yapmak için Internet Explorer 'da erişilebilir. MSXML, C++, JavaScript ve Visual Basic 6,0 dahil olmak üzere COM desteği olan herhangi bir programlama dilinden kullanılabilir.

MSXML, CLR 'ye dayalı yönetilen kodda kullanım için önerilmez.

## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML ve XmlLite karşılaştırması

XmlLite önbelleğe alma, iletme, çekme ayrıştırıcısıdır. Geliştiriciler öncelikle C++ ile XmlLite kullanır. Geliştiricilerin yönetilen kodla XmlLite kullanması önerilmez.

XmlLite 'ın başlıca avantajı, Çoğu senaryoda güvenli olan hafif ve hızlı bir XML ayrıştırıcısıdır. Tehdit yüzeyi alanı küçüktür. Güvenilmeyen belgeleri ayrıştırmanıza ve hizmet reddi ya da veri pozlaması gibi saldırılara karşı korunmak istiyorsanız, XmlLite iyi bir seçenek olabilir.

XmlLite, dil ile tümleşik sorgu (LINQ) ile tümleştirilebilir. Bu, LINQ 'ın arkasındaki zorlamaya yönelik programcı üretkenlik geliştirmelerini vermez.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML genel bakış](linq-xml-overview.md)
