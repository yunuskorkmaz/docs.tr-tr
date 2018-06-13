---
title: Geri Çağırma Metodu Olarak Bir Temsilci Hazırlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff875f2807a14493ab81a9e354b5c4dcdf3d5feb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389390"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Geri Çağırma Metodu Olarak Bir Temsilci Hazırlama
Bu örnek nasıl temsilciler işlev işaretçileri bekleniyor yönetilmeyen bir işleve nasıl iletileceğini gösterir. Temsilci bir yöntem başvuru içerebilir ve bir tür kullanımı uyumlu işlev işaretçisi ya da bir geri çağırma işlevini eşdeğer olan bir sınıftır.  
  
> [!NOTE]
>  Bir çağrı içinde bir temsilci kullandığınızda, ortak dil çalışma zamanı bu çağrı boyunca toplanan çöp olmaktan temsilci korur. Yönetilmeyen işlev çağrısı tamamlandıktan sonra kullanmak için temsilci depoluyorsa, temsilci ile yönetilmeyen işlev tamamlanana kadar ancak, el ile çöp toplama engellemeniz gerekir. Daha fazla bilgi için bkz: [HandleRef örnek](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) ve [GCHandle örnek](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).  
  
 Geri arama örneği kendi özgün işlevi bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
-   **TestCallBack** PinvokeLib.dll dışarı.  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   **TestCallBack2** PinvokeLib.dll dışarı.  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) daha önce listelenen işlevleri için bir uygulama içeren özel bir yönetilmeyen kitaplıktır.  
  
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
 [Çeşitli hazırlama örnekleri](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))  
 [Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
