---
title: XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma
description: XML 'yi yükleme veya ayrıştırma sırasında beyaz boşluk davranışını nasıl denetleyeceğinizi, özellikle de XML ağaçlarını dolduran yöntemlerin davranışını öğrenin.
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 3c044937d38f9f89ebc114af3eddbf5116c392ad
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302847"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>XML Yükleme veya Ayrıştırma Sırasında Boşluk Koruma
Bu konu, ' nin beyaz boşluk davranışının nasıl kontrol edileceğini açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (diğer bir deyişle, beyaz alanı korumadan), XML üzerinde bazı işlemleri gerçekleştirir ve ardından XML 'i girintilemeli olarak kaydeder. XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur. Bu varsayılan davranıştır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir. Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , XML 'i yüklediğinizde veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyabilirsiniz.  
  
 Bu konuda, XML ağaçlarını dolduran yöntemlerin beyaz boşluk davranışı açıklanmaktadır. XML ağaçlarını seri hale getirirken boşluk denetleme hakkında daha fazla bilgi için bkz. [serileştirilirken boşluk koruma](./preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>XML ağaçlarını dolduran yöntemlerin davranışı  
 <xref:System.Xml.Linq.XElement>Ve sınıflarında aşağıdaki yöntemler <xref:System.Xml.Linq.XDocument> bir xml ağacını dolduracaktır. Bir dosya, bir <xref:System.IO.TextReader> , bir veya bir dizeden BIR XML ağacını doldurabilirsiniz <xref:System.Xml.XmlReader> :  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Yöntem <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak kullanmıyorsa, Yöntem önemli olmayan boşlukları korumaz.  
  
 Çoğu durumda, yöntemi <xref:System.Xml.Linq.LoadOptions> bir bağımsız değişken olarak alırsa, isteğe bağlı boşluğu XML ağacında metin düğümleri olarak koruyabilirsiniz. Ancak, yöntemi bir öğesinden XML 'yi yüklüyorsanız, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader> boşluk olup olmayacağını belirler. Ayarın <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> hiçbir etkisi olmayacaktır.  
  
 Bu yöntemlerle, boşluk korununca, düğüm olarak XML ağacına önemli bir boşluk eklenir <xref:System.Xml.Linq.XText> . Boşluk korunmazsa, metin düğümleri eklenmez.  
  
 Kullanarak bir XML ağacı oluşturabilirsiniz <xref:System.Xml.XmlWriter> . Öğesine yazılan düğümler <xref:System.Xml.XmlWriter> ağaçta doldurulur. Ancak, bu yöntemi kullanarak bir XML ağacı oluşturduğunuzda, düğümün boşluk olup olmamasına veya boşluk olmasına bakılmaksızın tüm düğümler korunur.  
  