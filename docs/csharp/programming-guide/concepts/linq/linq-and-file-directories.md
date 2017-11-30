---
title: LINQ ve dosya dizinleri (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 62c7ee272c788ca687b84bb76a853e58f83f69ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-and-file-directories-c"></a>LINQ ve dosya dizinleri (C#)
Çok sayıda dosya sistemi işlemleri temelde sorgular ve bu nedenle LINQ yaklaşımı uymaktadır.  
  
 Bu bölümdeki sorguların bozucu olmayan olduğuna dikkat edin. Özgün dosya veya klasör içeriğini değiştirmek için kullanılmaz. Bu sorguları herhangi yan etkileri oluşmamalıdır kuralı izler. Genel olarak, kaynak verileri değiştiren (gerçekleştirmek dahil olmak üzere sorgular oluşturma / güncelleştirme / delete işleçleri) herhangi bir kod yalnızca verileri sorgular koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Nasıl yapılır: belirli bir öznitelik veya ad (C#) sahip dosyaları sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Bir veya daha fazla özelliklerini inceleyerek dosyalarını arayın gösterilmektedir, <xref:System.IO.FileInfo> nesnesi.  
  
 [Nasıl yapılır: dosyaları uzantıya (LINQ) (C#) göre gruplama](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Grupları döndürülecek gösterilmiştir <xref:System.IO.FileInfo> nesne dosya adı uzantılarına bağlı.  
  
 [Nasıl yapılır: sorgu için bir klasör (LINQ) (C#) kümesi bayt toplam sayısı](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Toplam bayt sayısı belirtilen dizin ağacında tüm dosyalar döndürmek gösterilmiştir.  
  
 [Nasıl yapılır: iki klasörün (LINQ) (C#) içeriğini karşılaştırma](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 İki belirtilen klasörlerde bulunan tüm dosyaları ve bir klasör ancak diğer var olan ayrıca tüm dosyaları geri dönmek gösterilmiştir.  
  
 [Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacında (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Nasıl bir dizin ağacındaki en büyük veya en küçük dosya veya dosyalar, belirtilen sayıda döndürüleceğini gösterir.  
  
 [Nasıl yapılır: sorgu (LINQ) (C#) bir dizin ağacında yineleyen dosyalar için](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Belirtilen dizin ağacında birden fazla konumda oluşan tüm dosya adları için Grup gösterilmektedir. Ayrıca özel bir karşılaştırıcı üzerinde göre daha karmaşık karşılaştırmaları gerçekleştirmek nasıl gösterir.  
  
 [Nasıl yapılır: (LINQ) (C#) bir klasördeki dosyaların içeriğini sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Bir ağaç klasörlerde yinelemek, her dosyasını açın ve dosyanın içeriğini sorgu gösterilmektedir.  
  
## <a name="comments"></a>Açıklamalar  
 Doğru dosya sistemi içeriğini temsil eder ve özel durumları düzgün bir şekilde işler bir veri kaynağı oluşturmaya dahil bazı karmaşıklık yoktur. Bu bölümdeki örnekleri bir anlık görüntü koleksiyonunu oluşturmak <xref:System.IO.FileInfo> belirtilen kök klasörü altındaki tüm dosyaları ve tüm alt klasörlerini temsil eden nesne. Her gerçek durumunu <xref:System.IO.FileInfo> ne zaman başlamalı ve bitmelidir bir sorgu yürütülürken arasında zaman içinde değişebilir. Örneğin, bir listesini oluşturabilirsiniz <xref:System.IO.FileInfo> nesneleri bir veri kaynağı olarak kullanın. Erişmeye çalıştığınızda `Length` özelliği bir sorgu <xref:System.IO.FileInfo> nesne değerini güncelleştirmek üzere dosya sisteminde erişmeye çalışır `Length`. Dosya artık alırsa bir <xref:System.IO.FileNotFoundException> sorgunuzda, rağmen değil sorgulama dosya sistemi doğrudan. Bu bölümde bazı sorgular, bazı durumlarda belirli bu özel durumlar tüketir ayrı bir yöntem kullanın. Başka bir seçeneği kullanarak dinamik olarak güncelleştirilen veri kaynağınız korumaktır <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to nesneler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
