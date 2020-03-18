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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138097"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Başlatma zamanında iş parçacığı oluşturma ve veri geçirme

Bir işletim sistemi işlemi oluşturulduğunda, işletim sistemi herhangi bir özgün uygulama etki alanı da dahil olmak üzere, bu işlemde kodu yürütmek için bir iş parçacığı enjekte eder. Bu noktadan itibaren, uygulama etki alanları oluşturulabilir ve herhangi bir işletim sistemi iş parçacığı mutlaka oluşturulma veya yok olmadan yok. Yürütülen kod yönetilirse, <xref:System.Threading.Thread> geçerli uygulama etki alanında çalıştırılan iş parçacığı için bir <xref:System.Threading.Thread.CurrentThread%2A> nesne türü <xref:System.Threading.Thread>statik özelliği alınarak elde edilebilir. Bu konu iş parçacığı oluşturma açıklar ve iş parçacığı yordamına veri aktarmak için alternatifleri açıklar.  
  
## <a name="creating-a-thread"></a>İş parçacığı oluşturma

 Yeni <xref:System.Threading.Thread> bir nesne oluşturmak yeni yönetilen iş parçacığı oluşturur. Sınıfın <xref:System.Threading.Thread> bir <xref:System.Threading.ThreadStart> temsilci veya <xref:System.Threading.ParameterizedThreadStart> temsilci alan oluşturucuları vardır; temsilci, <xref:System.Threading.Thread.Start%2A> yöntemi çağırdığınızda yeni iş parçacığı tarafından çağrılan yöntemi sarar. Birden <xref:System.Threading.Thread.Start%2A> fazla kez <xref:System.Threading.ThreadStateException> aramak bir atılmasını neden olur.  
  
 Yöntem, <xref:System.Threading.Thread.Start%2A> genellikle yeni iş parçacığı gerçekten başlamadan önce hemen döndürür. İş parçacığının <xref:System.Threading.Thread.ThreadState%2A> <xref:System.Threading.Thread.IsAlive%2A> durumunu herhangi bir anda belirlemek için ve özellikleri kullanabilirsiniz, ancak bu özellikler iş parçacıklarının etkinliklerini eşitlemek için asla kullanılmamalıdır.  
  
> [!NOTE]
> Bir iş parçacığı başlatıldıktan sonra, <xref:System.Threading.Thread> nesneye bir başvuru tutmak gerekmez. İş parçacığı yordamı sona erene kadar iş parçacığı yürütmeye devam ediyor.  
  
 Aşağıdaki kod örneği, başka bir nesne üzerinde örnek ve statik yöntemleri çağırmak için iki yeni iş parçacığı oluşturur.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>İş parçacıklarına veri aktarma

 .NET Framework sürüm <xref:System.Threading.ParameterizedThreadStart> 2.0'da, damad, <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemaşırı yüklemeyi çağırdığınızda veri içeren bir nesneyi iş parçacığına geçirmek için kolay bir yol sağlar. Kod <xref:System.Threading.ParameterizedThreadStart> örneği için bkz.  
  
 Delektin <xref:System.Threading.ParameterizedThreadStart> kullanılması veri aktarmak için tür <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> güvenli bir yol değildir, çünkü yöntem aşırı yük herhangi bir nesneyi kabul eder. Bir alternatif iş parçacığı yordamı ve verileri bir yardımcı sınıfta kapsüllemek ve iş parçacığı yordamını yürütmek için <xref:System.Threading.ThreadStart> temsilci kullanmaktır. Aşağıdaki örnekte bu tekniği gösterilmektedir:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ne <xref:System.Threading.ThreadStart> <xref:System.Threading.ParameterizedThreadStart> de temsilcinin bir geri dönüş değeri vardır, çünkü eşzamanlı bir çağrıdan verileri döndürecek bir yer yoktur. İş parçacığı yönteminin sonuçlarını almak için, bir sonraki bölümde gösterildiği gibi bir geri arama yöntemi kullanabilirsiniz.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Geri arama yöntemleriyle iş parçacığından veri alma

 Aşağıdaki örnek, iş parçacığından veri alan bir geri arama yöntemini gösterir. Verileri ve iş parçacığı yöntemini içeren sınıfın oluşturucusu da geri arama yöntemini temsil eden bir temsilci yi kabul eder; iş parçacığı yöntemi sona ermeden önce, geri arama temsilci çağırır.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [İş Parçacığı Oluşturma](index.md)
- [İş Parçacığı ve İş Parçacığı kullanma](using-threads-and-threading.md)
