---
title: 'Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f80f1903c4187a8da93d42ec6de363d097bcc37
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988177"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme
Bu örnekte, dosya dizinlerinde paralel hale getirmek işlemleri için iki basit yol gösterilmektedir. İlk sorgu, bir dizin <xref:System.IO.Directory.GetFiles%2A> ve tüm alt dizinler içindeki dosya adı dizisini doldurmak için yöntemini kullanır. Bu yöntem, tüm dizi dolduruluncaya kadar döndürmez ve bu nedenle işlemin başlangıcında gecikme süresini ortaya çıkarabilir. Ancak, dizi doldurulduktan sonra PLıNQ onu paralel olarak çok çabuk işleyebilir.  
  
 İkinci sorgu, sonuçları hemen döndürmeye <xref:System.IO.Directory.EnumerateDirectories%2A> başlayan <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> static ve yöntemleri kullanır. Bu yaklaşım, büyük dizin ağaçlarını yineleirken daha hızlı olabilir, ancak ilk örnekle karşılaştırılan işleme süresi birçok etkene bağlı olabilir.  
  
> [!WARNING]
> Bu örnekler, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ağaçtaki tüm dizinlere erişiminiz olduğunda basit senaryolarda dosya dizinlerinin nasıl yineleneceğini gösterir, dosya boyutları çok büyük değildir ve erişim süreleri önemli değildir. Bu yaklaşım, dosya adları dizisi oluşturulurken başlangıcında bir gecikme süresi içerir.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ağaçtaki tüm dizinlere erişiminiz olduğunda basit senaryolarda dosya dizinlerinin nasıl yineleneceğini gösterir, dosya boyutları çok büyük değildir ve erişim süreleri önemli değildir. Bu yaklaşım, önceki örnekteki sonuçları daha hızlı üretmeye başlar.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Kullanırken <xref:System.IO.Directory.GetFiles%2A>, ağaçtaki tüm dizinlerde yeterli izinlere sahip olduğunuzdan emin olun. Aksi takdirde, bir özel durum atılır ve hiçbir sonuç döndürülmeyecektir. Bir PLINQ <xref:System.IO.Directory.EnumerateDirectories%2A> sorgusunda kullanırken, yineleme devam etmenizi sağlamak için g/ç özel durumlarını düzgün bir şekilde işlemek sorunlu olur. Kodunuzun g/ç veya yetkisiz erişim özel durumlarını işlemesi gerekiyorsa, [nasıl yapılır: Dosya dizinlerini paralel sınıfla](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md)yineleyin.  
  
 G/ç gecikme süresi bir sorun ise (örneğin, ağ üzerinden dosya g/ç 'si), [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) ve bu [blog postasında](https://blogs.msdn.microsoft.com/pfxteam/2009/08/04/parallel-extensions-and-io/)açıklanan zaman uyumsuz g/ç tekniklerinden birini kullanmayı göz önünde bulundurun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
