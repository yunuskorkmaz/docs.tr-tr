---
title: XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: d015c21813df2224356bb49212fe282fa5372d03
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591547"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma
Bu konu, ' nin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]beyaz boşluk davranışının nasıl kontrol edileceğini açıklar.  
  
 Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (diğer bir deyişle, beyaz alanı korumadan), XML üzerinde bazı işlemleri gerçekleştirir ve ardından XML 'i girintilemeli olarak kaydeder. XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur. Bu varsayılan davranıştır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir. Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için, XML 'i yüklediğinizde veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyabilirsiniz.  
  
 Bu konuda, XML ağaçlarını dolduran yöntemlerin beyaz boşluk davranışı açıklanmaktadır. XML ağaçlarını seri hale getirirken boşluk denetleme hakkında daha fazla bilgi için bkz. [serileştirilirken boşluk koruma](./preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>XML ağaçlarını dolduran yöntemlerin davranışı  
 <xref:System.Xml.Linq.XElement> Ve<xref:System.Xml.Linq.XDocument> sınıflarında aşağıdaki yöntemler bir xml ağacını dolduracaktır. Bir dosya, bir <xref:System.IO.TextReader> <xref:System.Xml.XmlReader>, bir veya bir dizeden bir xml ağacını doldurabilirsiniz:  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Yöntem bir bağımsız değişken <xref:System.Xml.Linq.LoadOptions> olarak kullanmıyorsa, Yöntem önemli olmayan boşlukları korumaz.  
  
 Çoğu durumda, yöntemi bir bağımsız değişken olarak <xref:System.Xml.Linq.LoadOptions> alırsa, isteğe bağlı boşluğu XML ağacında metin düğümleri olarak koruyabilirsiniz. Ancak, yöntemi bir <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader> öğesinden XML 'yi yüklüyorsanız, boşluk olup olmayacağını belirler. Ayarın <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> hiçbir etkisi olmayacaktır.  
  
 Bu yöntemlerle, boşluk korununca, düğüm olarak <xref:System.Xml.Linq.XText> XML ağacına önemli bir boşluk eklenir. Boşluk korunmazsa, metin düğümleri eklenmez.  
  
 Kullanarak bir XML ağacı oluşturabilirsiniz <xref:System.Xml.XmlWriter>. Öğesine <xref:System.Xml.XmlWriter> yazılan düğümler ağaçta doldurulur. Ancak, bu yöntemi kullanarak bir XML ağacı oluşturduğunuzda, düğümün boşluk olup olmamasına veya boşluk olmasına bakılmaksızın tüm düğümler korunur.  
  