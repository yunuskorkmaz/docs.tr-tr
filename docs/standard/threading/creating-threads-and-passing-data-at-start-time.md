---
title: Başlatma zamanında iş parçacığı oluşturma ve veri geçirme
description: .NET 'teki bir işletim sistemi işleminin başlangıç saatinde iş parçacıkları oluşturmayı ve verileri nasıl geçibileceğinizi anlayın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
ms.openlocfilehash: 811028d3c853441ff3a61d3628a44e5c65ba7059
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661920"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Başlatma zamanında iş parçacığı oluşturma ve veri geçirme

Bir işletim sistemi işlemi oluşturulduğunda, işletim sistemi, özgün uygulama etki alanı dahil olmak üzere, bu işlemdeki kodu yürütmek için bir iş parçacığını çıkartır. Bu noktadan itibaren, uygulama etki alanları, herhangi bir işletim sistemi iş parçacığı oluşturulması veya yok olması gerekmeden oluşturulabilir ve yok edilebilir. Yürütülen kod yönetilen kodse, <xref:System.Threading.Thread> geçerli uygulama etki alanında yürütülen iş parçacığına ait bir nesne, türünün statik özelliği alınırken elde edilebilir <xref:System.Threading.Thread.CurrentThread%2A> <xref:System.Threading.Thread> . Bu konu, iş parçacığı oluşturma işlemini açıklar ve iş parçacığı yordamına veri geçirme alternatiflerini açıklar.  
  
## <a name="creating-a-thread"></a>İş parçacığı oluşturma

 Yeni bir <xref:System.Threading.Thread> nesne oluşturmak yeni bir yönetilen iş parçacığı oluşturur. <xref:System.Threading.Thread>Sınıf, bir <xref:System.Threading.ThreadStart> temsilci veya temsilci alan oluşturuculara sahiptir <xref:System.Threading.ParameterizedThreadStart> ; temsilci, yöntemini çağırdığınızda yeni iş parçacığı tarafından çağrılan yöntemi sarar <xref:System.Threading.Thread.Start%2A> . Birden <xref:System.Threading.Thread.Start%2A> çok kez çağırma bir, oluşturulmasına neden olur <xref:System.Threading.ThreadStateException> .  
  
 <xref:System.Threading.Thread.Start%2A>Yöntemi hemen, genellikle yeni iş parçacığı başlamadan önce döndürülür. <xref:System.Threading.Thread.ThreadState%2A> <xref:System.Threading.Thread.IsAlive%2A> İş parçacığının durumunu herhangi bir anda anlamak için ve özelliklerini kullanabilirsiniz, ancak bu özellikler hiçbir zaman iş parçacığı etkinliklerini eşitlemek için kullanılmamalıdır.  
  
> [!NOTE]
> Bir iş parçacığı başlatıldıktan sonra, nesnesine bir başvuru tutulması gerekli değildir <xref:System.Threading.Thread> . İş parçacığı yordamı sona erene kadar iş parçacığı yürütülmeye devam eder.  
  
 Aşağıdaki kod örneği, başka bir nesne üzerinde örnek ve statik yöntemleri çağırmak için iki yeni iş parçacığı oluşturur.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>İş parçacıklarına veri geçirme

 .NET Framework sürüm 2,0 ' de temsilci, <xref:System.Threading.ParameterizedThreadStart> yöntem aşırı yüklemesini çağırdığınızda bir iş parçacığına veri içeren bir nesneyi geçirmek için kolay bir yol sağlar <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> . <xref:System.Threading.ParameterizedThreadStart>Kod örneği için bkz..  
  
 <xref:System.Threading.ParameterizedThreadStart> <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> Yöntem aşırı yüklemesi herhangi bir nesneyi kabul ettiğinden, temsilcinin kullanılması, verileri geçirmek için tür açısından güvenli bir yoldur. Diğer bir seçenek de iş parçacığı yordamını ve verileri bir yardımcı sınıfında kapsüllemek ve <xref:System.Threading.ThreadStart> iş parçacığı yordamını yürütmek için temsilciyi kullanmaktır. Aşağıdaki örnek bu tekniği göstermektedir:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ne <xref:System.Threading.ThreadStart> ya da <xref:System.Threading.ParameterizedThreadStart> temsilcinin dönüş değeri yoktur, çünkü verileri zaman uyumsuz bir çağrıdan döndürmek için bir yer yoktur. Bir iş parçacığı yönteminin sonuçlarını almak için, sonraki bölümde gösterildiği gibi bir geri çağırma yöntemi kullanabilirsiniz.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Geri çağırma yöntemleriyle iş parçacıklarından veri alma

 Aşağıdaki örnek, bir iş parçacığından veri alan bir geri çağırma yöntemi gösterir. Veri ve iş parçacığı yöntemi içeren sınıf için Oluşturucu, geri çağırma yöntemini temsil eden bir temsilciyi de kabul eder; iş parçacığı yöntemi bitmeden önce geri çağırma temsilcisini çağırır.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [İş Parçacığı Oluşturma](index.md)
- [Iş parçacıkları ve Iş parçacığı kullanma](using-threads-and-threading.md)
