---
title: İş parçacığı oluşturma ve başlatma zamanında veri geçirme
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028f8b978a7809fa9ae4710ab85d7dc84e7b04fc
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275528"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>İş parçacığı oluşturma ve başlatma zamanında veri geçirme

İşletim sistemi, bir işletim sistemi işlem oluşturulduğunda, özgün tüm uygulama etki alanı da dahil olmak üzere bu işlemde kod yürütmek için bir iş parçacığı ekler. Bu noktadan itibaren uygulama etki alanları oluşturulabilir ve mutlaka yok veya oluşturulan tüm işletim sistemleri iş parçacıkları yok. Yürütülen kod yönetilen kod, bir <xref:System.Threading.Thread> parçacığının geçerli uygulama etki alanında statik alarak elde edilebilir nesnesi <xref:System.Threading.Thread.CurrentThread%2A> türünün özelliği <xref:System.Threading.Thread>. Bu konu, iş parçacığı oluşturma açıklar ve iş parçacığı yordamı için verileri geçirmek için seçenekleri açıklar.  
  
## <a name="creating-a-thread"></a>Bir iş parçacığı oluşturma

 Yeni bir oluşturma <xref:System.Threading.Thread> yeni bir yönetilen iş parçacığı nesnesi oluşturur. <xref:System.Threading.Thread> Sınıfında alan oluşturucular bir <xref:System.Threading.ThreadStart> temsilci veya <xref:System.Threading.ParameterizedThreadStart> temsilci; çağırdığınızda, yeni iş parçacığı tarafından çağrılan yöntem temsilciye sarmalar <xref:System.Threading.Thread.Start%2A> yöntemi. Çağırma <xref:System.Threading.Thread.Start%2A> birden çok kez neden olan bir <xref:System.Threading.ThreadStateException> oluşturulması için.  
  
 <xref:System.Threading.Thread.Start%2A> Yöntemi, hemen, genellikle yeni iş parçacığı gerçekten başlatılmadan önce döndürür. Kullanabileceğiniz <xref:System.Threading.Thread.ThreadState%2A> ve <xref:System.Threading.Thread.IsAlive%2A> herhangi bir anda iş parçacığı durumunu belirlemek için özellikleri, ancak bu özellikler hiçbir zaman iş parçacıklarının etkinlikleri eşitlemek için kullanılmamalıdır.  
  
> [!NOTE]
> Bir iş parçacığı başlatıldıktan sonra bir başvuru korumak gerekli değildir <xref:System.Threading.Thread> nesne. İş parçacığının iş parçacığı yordamı sonlandırılana kadar yürütmeye devam eder.  
  
 Aşağıdaki kod örneği, örnek ve statik yöntemler, başka bir nesne üzerinde çağırmak için iki yeni iş parçacığı oluşturur.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>İş parçacıklarına veri geçirme

 .NET Framework sürüm 2.0 <xref:System.Threading.ParameterizedThreadStart> temsilci çağırdığınızda, bir iş parçacığına veri içeren bir nesne geçirmek için kolay bir yol sağlar <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi. Bkz: <xref:System.Threading.ParameterizedThreadStart> kod örneği için.  
  
 Kullanarak <xref:System.Threading.ParameterizedThreadStart> temsilci değil veri iletmek için tür açısından güvenli bir şekilde çünkü <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini kabul eden herhangi bir nesne. İş parçacığı yordamı ve yardımcı bir sınıf içindeki verileri kapsüllemek ve kullanmak için bir alternatifidir <xref:System.Threading.ThreadStart> iş parçacığı yordamı yürütmek için temsilci. Aşağıdaki örnek, bu tekniği gösterir:

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ne <xref:System.Threading.ThreadStart> ya da <xref:System.Threading.ParameterizedThreadStart> temsilcinin dönüş değeri, zaman uyumsuz bir çağrıdan dönüş verileri bir yer olduğundan. Bir iş parçacığı yöntem sonuçlarını almak için sonraki bölümde gösterildiği gibi bir geri çağırma yöntemi kullanabilirsiniz.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Geri çağırma yöntemleri ile parçacıklarından veri alma

 Aşağıdaki örnek, bir iş parçacığından verileri alan bir geri arama yöntemi gösterir. Verileri ve iş parçacığı yöntemi içeren sınıf için oluşturucu, aynı zamanda geri çağırma yöntemi temsil eden bir temsilci kabul eder; iş parçacığı yöntemi sona ermeden önce geri çağırma temsilcisini çağırır.  
  
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
