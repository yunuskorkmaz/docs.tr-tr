---
title: "Geri Çağırma Metodu Olarak Bir Temsilci Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 894445657c938d381a8585c5e9c7440c694aa5b1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Geri Çağırma Metodu Olarak Bir Temsilci Hazırlama
Bu örnek nasıl temsilciler işlev işaretçileri bekleniyor yönetilmeyen bir işleve nasıl iletileceğini gösterir. Temsilci bir yöntem başvuru içerebilir ve bir tür kullanımı uyumlu işlev işaretçisi ya da bir geri çağırma işlevini eşdeğer olan bir sınıftır.  
  
> [!NOTE]
>  Bir çağrı içinde bir temsilci kullandığınızda, ortak dil çalışma zamanı bu çağrı boyunca toplanan çöp olmaktan temsilci korur. Yönetilmeyen işlev çağrısı tamamlandıktan sonra kullanmak için temsilci depoluyorsa, temsilci ile yönetilmeyen işlev tamamlanana kadar ancak, el ile çöp toplama engellemeniz gerekir. Daha fazla bilgi için bkz: [HandleRef örnek](http://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959) ve [GCHandle örnek](http://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f).  
  
 Geri arama örneği kendi özgün işlevi bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
-   **TestCallBack** PinvokeLib.dll dışarı.  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   **TestCallBack2** PinvokeLib.dll dışarı.  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614) daha önce listelenen işlevleri için bir uygulama içeren özel bir yönetilmeyen kitaplıktır.  
  
 Bu örnekte `LibWrap` sınıfı için yönetilen prototipleri içerir `TestCallBack` ve `TestCallBack2` yöntemleri. Her iki yöntem de bir temsilci için bir geri çağırma işlevi parametre olarak geçirin. Temsilci imza başvurduğu yöntemi imzası eşleşmesi gerekir. Örneğin, `FPtr` ve `FPtr2` temsilciler sahip aynı imza `DoSomething` ve `DoSomething2` yöntemleri.  
  
## <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çeşitli hazırlama örnekleri](http://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [Platform çağırma veri türleri](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [Yönetilen Kodda Prototipler Oluşturma](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
