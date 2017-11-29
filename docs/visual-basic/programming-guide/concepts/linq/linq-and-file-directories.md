---
title: LINQ ve dosya dizinleri (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 470ad8e783eb05cc56949982b2d2d79d5aaefdc2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ ve dosya dizinleri (Visual Basic)
Çok sayıda dosya sistemi işlemleri temelde sorgular ve bu nedenle LINQ yaklaşımı uymaktadır.  
  
 Bu bölümdeki sorguların bozucu olmayan olduğuna dikkat edin. Özgün dosya veya klasör içeriğini değiştirmek için kullanılmaz. Bu sorguları herhangi yan etkileri oluşmamalıdır kuralı izler. Genel olarak, kaynak verileri değiştiren (gerçekleştirmek dahil olmak üzere sorgular oluşturma / güncelleştirme / delete işleçleri) herhangi bir kod yalnızca verileri sorgular koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Nasıl yapılır: belirli bir öznitelik veya ad (Visual Basic) sahip dosyaları sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Bir veya daha fazla özelliklerini inceleyerek dosyalarını arayın gösterilmektedir, <xref:System.IO.FileInfo> nesnesi.  
  
 [Nasıl yapılır: dosyaları uzantıya (LINQ) (Visual Basic) göre gruplama](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Grupları döndürülecek gösterilmiştir <xref:System.IO.FileInfo> nesne dosya adı uzantılarına bağlı.  
  
 [Nasıl yapılır: sorgu için bir klasör (LINQ) (Visual Basic) kümesi bayt toplam sayısı](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 Toplam bayt sayısı belirtilen dizin ağacında tüm dosyalar döndürmek gösterilmiştir.  
  
 [Nasıl yapılır: iki klasörün (LINQ) (Visual Basic) içeriğini karşılaştırma](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 İki belirtilen klasörlerde bulunan tüm dosyaları ve bir klasör ancak diğer var olan ayrıca tüm dosyaları geri dönmek gösterilmiştir.  
  
 [Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 Nasıl bir dizin ağacındaki en büyük veya en küçük dosya veya dosyalar, belirtilen sayıda döndürüleceğini gösterir.  
  
 [Nasıl yapılır: sorgu (LINQ) (Visual Basic) bir dizin ağacında yineleyen dosyalar için](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Belirtilen dizin ağacında birden fazla konumda oluşan tüm dosya adları için Grup gösterilmektedir. Ayrıca özel bir karşılaştırıcı üzerinde göre daha karmaşık karşılaştırmaları gerçekleştirmek nasıl gösterir.  
  
 [Nasıl yapılır: (LINQ) (Visual Basic) bir klasördeki dosyaların içeriğini sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 Bir ağaç klasörlerde yinelemek, her dosyasını açın ve dosyanın içeriğini sorgu gösterilmektedir.  
  
## <a name="comments"></a>Açıklamalar  
 Doğru dosya sistemi içeriğini temsil eder ve özel durumları düzgün bir şekilde işler bir veri kaynağı oluşturmaya dahil bazı karmaşıklık yoktur. Bu bölümdeki örnekleri bir anlık görüntü koleksiyonunu oluşturmak <xref:System.IO.FileInfo> belirtilen kök klasörü altındaki tüm dosyaları ve tüm alt klasörlerini temsil eden nesne. Her gerçek durumunu <xref:System.IO.FileInfo> ne zaman başlamalı ve bitmelidir bir sorgu yürütülürken arasında zaman içinde değişebilir. Örneğin, bir listesini oluşturabilirsiniz <xref:System.IO.FileInfo> nesneleri bir veri kaynağı olarak kullanın. Erişmeye çalıştığınızda `Length` özelliği bir sorgu <xref:System.IO.FileInfo> nesne değerini güncelleştirmek üzere dosya sisteminde erişmeye çalışır `Length`. Dosya artık alırsa bir <xref:System.IO.FileNotFoundException> sorgunuzda, rağmen değil sorgulama dosya sistemi doğrudan. Bu bölümde bazı sorgular, bazı durumlarda belirli bu özel durumlar tüketir ayrı bir yöntem kullanın. Başka bir seçeneği kullanarak dinamik olarak güncelleştirilen veri kaynağınız korumaktır <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
