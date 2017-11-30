---
title: "Başlatma Zamanında İş Parçacığı Oluşturma ve Veri Geçirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Başlatma Zamanında İş Parçacığı Oluşturma ve Veri Geçirme
Bir işletim sistemi işlem oluşturulduğunda, işletim sistemi herhangi bir özgün uygulama etki alanı dahil olmak üzere bu işlemde kod yürütmek için bir iş parçacığı yerleştirir. Bu noktadan itibaren uygulama etki alanları oluşturulur ve mutlaka oluşturulma veya yok tüm işletim sistemi iş parçacıkları yok. Yürütülen kod yönetiliyorsa kod, sonra bir <xref:System.Threading.Thread> geçerli uygulama etki alanında iş parçacığının statik alarak elde edilebilir için nesne <xref:System.Threading.Thread.CurrentThread%2A> türündeki özelliği <xref:System.Threading.Thread>. Bu konu, iş parçacığı oluşturma açıklar ve iş parçacığı yordamı veri geçirme için seçenekleri açıklar.  
  
## <a name="creating-a-thread"></a>Bir iş parçacığı oluşturma  
 Yeni bir oluşturma <xref:System.Threading.Thread> yeni bir yönetilen iş parçacığı nesnesi oluşturur. <xref:System.Threading.Thread> Sınıfına sahip olması oluşturucular bir <xref:System.Threading.ThreadStart> temsilci veya <xref:System.Threading.ParameterizedThreadStart> temsilci; çağırdığınızda yeni iş parçacığı tarafından çağrılan yöntemin temsilci sarmalar <xref:System.Threading.Thread.Start%2A> yöntemi. Çağırma <xref:System.Threading.Thread.Start%2A> birden çok kez neden olan bir <xref:System.Threading.ThreadStateException> oluşturulmasına.  
  
 <xref:System.Threading.Thread.Start%2A> Yöntemi, hemen, genellikle yeni bir iş parçacığı gerçekten başlatılmadan önce döndürür. Kullanabileceğiniz <xref:System.Threading.Thread.ThreadState%2A> ve <xref:System.Threading.Thread.IsAlive%2A> iş parçacığı herhangi bir anda durumunu belirlemek için özellikler, ancak bu özellikler hiçbir iş parçacığı etkinliklerini eşitlemek için kullanılmalıdır.  
  
> [!NOTE]
>  Bir iş parçacığı başladıktan sonra bir başvuru korumak gerekli değildir <xref:System.Threading.Thread> nesnesi. İş parçacığı için iş parçacığı yordamı sonlanana kadar yürütmeye devam eder.  
  
 Aşağıdaki kod örneği başka bir nesne üzerinde örnek ve statik yöntemleri çağırmak için iki yeni iş parçacığı oluşturur.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>İş parçacıklarına veri geçirme ve parçacıklarından veri alma  
 .NET Framework sürüm 2.0, <xref:System.Threading.ParameterizedThreadStart> temsilci çağırdığınızda bir iş parçacığı verileri içeren bir nesne geçirmek için kolay bir yol sağlar <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini. Bkz: <xref:System.Threading.ParameterizedThreadStart> için bir kod örneğidir.  
  
 Kullanarak <xref:System.Threading.ParameterizedThreadStart> temsilci değil veri iletmek için bir tür kullanımı uyumlu şekilde çünkü <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini kabul eden herhangi bir nesne. İş parçacığı yordamı ve bir yardımcı sınıfı verileri şifreleyebilir ve kullanmak için bir alternatif olan <xref:System.Threading.ThreadStart> iş parçacığı yordamı yürütmek için temsilci. Bu teknik izleyen iki kod örnekleri gösterilir.  
  
 Hiçbirini temsilcileri olan dönüş değeri, zaman uyumsuz çağrısından verileri döndürmek için hiçbir yerde olduğundan. Bir iş parçacığı yöntem sonuçlarını almak için ikinci kod örneğinde gösterildiği gibi bir geri çağırma yöntemi kullanabilirsiniz.  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>Geri arama yöntemleri ile veri alma  
 Aşağıdaki örnek, bir iş parçacığından veri alan geri arama yöntemi gösterir. Verileri ve iş parçacığı yöntemi içeren sınıf oluşturucusu geri çağırma yöntemi temsil eden bir temsilci de kabul eder; iş parçacığı yöntemi sona ermeden önce geri çağırma temsilcisini çağırır.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş parçacığı kullanma ve iş parçacığı oluşturma](../../../docs/standard/threading/using-threads-and-threading.md)
