---
title: LINQ ve dosya dizinleri (C#)
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: 4bdd21cf4d8558f140b265f195368082964c34c4
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514891"
---
# <a name="linq-and-file-directories-c"></a>LINQ ve dosya dizinleri (C#)
Çok sayıda dosya sistemi işlemleri temelde sorgular ve bu nedenle LINQ yaklaşım için çok uygundur.  
  
 Bu bölümdeki sorguların bozucu olmayan olduğunu unutmayın. Özgün dosya ve klasörlerin içeriğini değiştirmek için kullanılmaz. Bu sorgu tüm yan etkileri oluşmamalıdır kuralı izler. Genel olarak, kaynak verileri değiştiren (gerçekleştirmek de dahil olmak üzere sorguları oluşturma / güncelleştirme / delete işleçleri) herhangi bir kod yalnızca verileri sorgular koddan ayrı tutulmalıdır.  
  
 Bu bölüm aşağıdaki konular içerir:  
  
 [Nasıl yapılır: belirli bir öznitelik veya ada (C#) sahip dosyaları sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 Bir veya daha fazla özelliklerini inceleyerek dosyalarının aranacağı gösterilmektedir, <xref:System.IO.FileInfo> nesne.  
  
 [Nasıl yapılır: dosyaları uzantıya (LINQ) (C#) göre gruplama](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 Grupları döndürülecek gösterilmektedir <xref:System.IO.FileInfo> nesne dosya adı uzantılarına bağlı.  
  
 [Nasıl yapılır: sorgu klasörleri (LINQ) (C#) bir dizi bayt toplam sayısı](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 Toplam bayt sayısı belirtilen dizin ağacındaki tüm dosyaları döndürmek gösterilmektedir.  
  
 [Nasıl yapılır: iki klasörün (LINQ) (C#) içeriğini karşılaştırma](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 Belirtilen iki klasörlerinde bulunan tüm dosyaları ve bir klasör ancak diğer mevcut olan ayrıca tüm dosyaları iade işlemi gösterilmektedir.  
  
 [Nasıl yapılır: sorgu için en büyük dosya veya dosyalar bir dizin ağacındaki (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 Nasıl bir dizin ağacındaki en büyük veya en küçük dosya veya dosyalar, belirtilen sayıda döndürüleceğini gösterir.  
  
 [Nasıl yapılır: sorgu (LINQ) (C#) bir dizin ağacında yineleyen dosyalar için](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 Belirtilen dizin ağacı birden fazla konumda gerçekleşen tüm dosya adları için gruplandırma işlemi gösterilmektedir. Ayrıca özel bir karşılaştırıcı üzerinde dayalı daha karmaşık karşılaştırmalar yapmak nasıl gösterir.  
  
 [Nasıl yapılır: (LINQ) (C#) bir klasördeki dosyaların içeriğini sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 Bir ağaç klasörlerinde yinelemek, her dosyasını açın ve dosyanın içeriğini sorgu işlemi gösterilmektedir.  
  
## <a name="comments"></a>Açıklamalar  
 Bir veri kaynağı doğru bir şekilde dosya sistemi içeriğini temsil eder ve düzgün bir şekilde özel durumları işler oluşturmak için gerekli olan bazı karmaşıklığı yoktur. Bu bölümdeki örneklerde, bir anlık görüntü koleksiyonunu oluşturmak <xref:System.IO.FileInfo> belirtilen kök klasör altındaki tüm dosyaları ve tüm alt klasörlerindeki temsil eden nesneleri. Her gerçek durumuyla <xref:System.IO.FileInfo> ne zaman başlar ve son Sorguyu yürüten arasında zaman içinde değişebilir. Örneğin, bir listesini oluşturabilirsiniz <xref:System.IO.FileInfo> veri kaynağı olarak kullanılacak nesne. Erişmeye çalışırsanız `Length` özelliği bir sorgu <xref:System.IO.FileInfo> nesne değerini güncelleştirmek üzere dosya sisteminde erişmeye çalışır `Length`. Dosya artık mevcut değilse, erişmenizi sağlayacak bir <xref:System.IO.FileNotFoundException> sorgunuzda, olsa bile, yok sorguladığınız dosya sistemi doğrudan. Bu bölümde bazı sorgular, bu belirli özel durumları, bazı durumlarda tüketen ayrı bir yöntem kullanın. Başka bir seçeneği kullanarak dinamik olarak güncelleştirilen veri kaynağınız tutmaktır <xref:System.IO.FileSystemWatcher>.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ to Objects'in (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
