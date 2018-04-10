---
title: 'Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 523db9d356954a4a397b63d836018070effa9e5b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Nasıl yapılır: PLINQ ile Dosya Dizinlerini Yineleme
Bu örnek, dosya dizinleri işlemleri paralel hale iki basit yol gösterir. İlk sorguyu kullanan <xref:System.IO.Directory.GetFiles%2A> bir dizinde ve tüm alt dizinler dosya adlarının dizisini doldurmak için yöntem. Bu yöntem, tüm diziyi doldurulur ve bu nedenle işlemin başında gecikme getirebilir kadar döndürmez. Dizi doldurulduktan sonra ancak PLINQ, paralel olarak çok hızlı bir şekilde işleyebilir.  
  
 İkinci sorguyu statik kullanan <xref:System.IO.Directory.EnumerateDirectories%2A> ve <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> sonuçları hemen döndürülmesini yöntemleri. Büyük directory ağaçlarında dolaşırken ilk örneği işleme süresinde birçok faktöre bağlıdır rağmen bu yaklaşım daha hızlı olabilir.  
  
> [!WARNING]
>  Bu örnekler kullanım göstermek için tasarlanmıştır ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir. Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm dizinler ağacında erişimi, dosya boyutları çok büyük olmayan ve erişim zamanları önemli olmadıkları zaman dosya dizinleri basit senaryolarda üzerinden yineleme gösterir. Dosya adları dizisi oluşturulan sırada bu yaklaşım gecikme başında nokta içerir.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tüm dizinler ağacında erişimi, dosya boyutları çok büyük olmayan ve erişim zamanları önemli olmadıkları zaman dosya dizinleri basit senaryolarda üzerinden yineleme gösterir. Bu yaklaşım, önceki örnekte daha hızlı sonuçlar üretir başlar.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Kullanırken <xref:System.IO.Directory.GetFiles%2A>, ağacında tüm dizinlerde yeterli izinlere sahip olduğundan emin olun. Aksi takdirde bir özel durum ve hiç sonuç döndürmedi. Kullanırken <xref:System.IO.Directory.EnumerateDirectories%2A> bir PLINQ sorgusunda yineleme devam etmenizi sağlayan normal şekilde g/ç özel durumları işleme sorunlu oluşturur. Kodunuzu g/ç veya yetkisiz erişim özel durumlarını işlemelidir sonra açıklanan yaklaşımı düşünmelisiniz [nasıl yapılır: paralel sınıfla dosya dizinlerini yineleme](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 G/ç gecikmesi bir sorun ise, örneğin bir ağ üzerinden dosya g/ç ile açıklanan zaman uyumsuz g/ç teknikleri birini kullanmayı [TPL ve geleneksel .NET Framework zaman uyumsuz Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) ve bu [blog gönderisi ](https://blogs.msdn.microsoft.com/pfxteam/2009/08/04/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
