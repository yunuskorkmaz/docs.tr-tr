---
title: 'Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d48f6df1e0e7680d2706c73c33dc817e1feaf1d5
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517755"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme
Bu örnek dosya dizinleri işlemler paralel hale getirmek için iki basit yol gösterir. İlk sorgu kullanan <xref:System.IO.Directory.GetFiles%2A> dosya adlarında bir dizin ve tüm alt dizinler bir dizi doldurmak için yöntemi. Bu yöntem, tüm dizi doldurulur ve bu nedenle işlemin başında gecikme ortaya çıkarabilir kadar döndürmez. Dizi doldurulduktan sonra Bununla birlikte, PLINQ, paralel olarak çok hızlı bir şekilde işleyebilir.  
  
 İkinci sorgu statik kullanan <xref:System.IO.Directory.EnumerateDirectories%2A> ve <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> sonuçları hemen döndürülmesini yöntemleri. Büyük bir dizin ağaçlara göre dolaşırken ilk örnek için işleme süresinde birçok faktöre bağlıdır ancak bu yaklaşım daha hızlı olabilir.  
  
> [!WARNING]
>  Bu örnekler kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir. Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm dizin ağacında erişiminiz, dosya boyutu çok büyük değildir ve erişim zamanları önemli olmayan dosya dizinleri basit senaryolar üzerinden yinelemek gösterilmektedir. Dosya adları dizisi oluşturulur ancak bu yaklaşım bir süre başına düşük gecikme süresi gerektirir.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm dizin ağacında erişiminiz, dosya boyutu çok büyük değildir ve erişim zamanları önemli olmayan dosya dizinleri basit senaryolar üzerinden yinelemek gösterilmektedir. Bu yaklaşım, önceki örnekten daha hızlı sonuçlar üreten başlar.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Kullanırken <xref:System.IO.Directory.GetFiles%2A>, tüm dizinlerde ağacında yeterli izinlere sahip olduğunuzdan emin olun. Aksi halde bir özel durum ve hiçbir sonuç döndürmedi. Kullanırken <xref:System.IO.Directory.EnumerateDirectories%2A> bir PLINQ sorgusu yineleme devam etmenize olanak sağlayan düzgün bir şekilde g/ç özel durumları işlemek için sorunlu. Kodunuz g/ç veya yetkisiz erişimi özel durumlarını işlemelidir sonra açıklanan yaklaşımı düşünmelisiniz [nasıl yapılır: paralel sınıfla dosya dizinlerini yineleme](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 G/ç gecikmesi sorunu yaşıyorsanız, örneğin bir ağ üzerinden dosya g/ç ile açıklanan zaman uyumsuz g/ç tekniklerden birini kullanmayı [TPL ve geleneksel .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) ve bu [blog gönderisi ](https://blogs.msdn.microsoft.com/pfxteam/2009/08/04/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
