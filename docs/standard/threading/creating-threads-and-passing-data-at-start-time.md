---
title: Başlatma zamanında iş parçacığı oluşturma ve veri geçirme
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
ms.openlocfilehash: a628cbb4c9ec8e1c9ccd9fd73e72a82ecf2b2836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138097"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Başlatma zamanında iş parçacığı oluşturma ve veri geçirme

Bir işletim sistemi işlemi oluşturulduğunda, işletim sistemi, özgün uygulama etki alanı dahil olmak üzere, bu işlemdeki kodu yürütmek için bir iş parçacığını çıkartır. Bu noktadan itibaren, uygulama etki alanları, herhangi bir işletim sistemi iş parçacığı oluşturulması veya yok olması gerekmeden oluşturulabilir ve yok edilebilir. Yürütülen kod yönetilen kod ise, geçerli uygulama etki alanında yürütülen iş parçacığının <xref:System.Threading.Thread> nesnesi, <xref:System.Threading.Thread>türündeki statik <xref:System.Threading.Thread.CurrentThread%2A> özelliği aracılığıyla elde edilebilir. Bu konu, iş parçacığı oluşturma işlemini açıklar ve iş parçacığı yordamına veri geçirme alternatiflerini açıklar.  
  
## <a name="creating-a-thread"></a>İş parçacığı oluşturma

 Yeni bir <xref:System.Threading.Thread> nesnesi oluşturma yeni bir yönetilen iş parçacığı oluşturur. <xref:System.Threading.Thread> sınıfı, bir <xref:System.Threading.ThreadStart> temsilcisi veya <xref:System.Threading.ParameterizedThreadStart> temsilcisi alan oluşturuculara sahiptir; temsilci, <xref:System.Threading.Thread.Start%2A> yöntemini çağırdığınızda yeni iş parçacığı tarafından çağrılan yöntemi sarmalanmış. <xref:System.Threading.Thread.Start%2A> birden çok kez çağırmak <xref:System.Threading.ThreadStateException> oluşturulmasına neden olur.  
  
 <xref:System.Threading.Thread.Start%2A> yöntemi hemen, genellikle yeni iş parçacığı başlamadan önce döndürülür. İş parçacığının durumunu herhangi bir anda anlamak için <xref:System.Threading.Thread.ThreadState%2A> ve <xref:System.Threading.Thread.IsAlive%2A> özelliklerini kullanabilirsiniz, ancak bu özellikler hiçbir zaman iş parçacığı etkinliklerini eşitlemek için kullanılmamalıdır.  
  
> [!NOTE]
> Bir iş parçacığı başlatıldıktan sonra, <xref:System.Threading.Thread> nesnesine bir başvuru tutulması gerekli değildir. İş parçacığı yordamı sona erene kadar iş parçacığı yürütülmeye devam eder.  
  
 Aşağıdaki kod örneği, başka bir nesne üzerinde örnek ve statik yöntemleri çağırmak için iki yeni iş parçacığı oluşturur.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>İş parçacıklarına veri geçirme

 .NET Framework sürüm 2,0 ' de, <xref:System.Threading.ParameterizedThreadStart> temsilci <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntem aşırı yüklemesini çağırdığınızda bir iş parçacığına veri içeren bir nesneyi geçirmek için kolay bir yol sağlar. Kod örneği için <xref:System.Threading.ParameterizedThreadStart> bakın.  
  
 <xref:System.Threading.ParameterizedThreadStart> temsilcinin kullanılması, verileri geçirmek için tür açısından güvenli bir yoldur; çünkü <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi herhangi bir nesneyi kabul eder. Diğer bir seçenek de iş parçacığı yordamını ve verileri bir yardımcı sınıfında kapsüllemek ve iş parçacığı yordamını yürütmek için <xref:System.Threading.ThreadStart> temsilcisini kullanmaktır. Aşağıdaki örnek bu tekniği göstermektedir:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Bir zaman uyumsuz çağrıdan verileri döndürmek için hiçbir yer olmadığından <xref:System.Threading.ThreadStart> ve <xref:System.Threading.ParameterizedThreadStart> temsilcisinin dönüş değeri yoktur. Bir iş parçacığı yönteminin sonuçlarını almak için, sonraki bölümde gösterildiği gibi bir geri çağırma yöntemi kullanabilirsiniz.
  
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
- [İş parçacığı oluşturma](index.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](using-threads-and-threading.md)
