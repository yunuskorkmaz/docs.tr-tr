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
ms.openlocfilehash: 2aa999199ddf11a1a2db57b6f7b1dd198b4ea61d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529853"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Geri Çağırma Metodu Olarak Bir Temsilci Hazırlama
Bu örnek, temsilciler işlev işaretçileri bekleniyor yönetilmeyen bir işleve geçirilecek gösterilmiştir. Bir temsilci, bir yönteme başvuru içerebilir ve bir tür açısından güvenli bir işlev işaretçisine veya geri çağırma işlevi için eşdeğer bir gruba bir sınıftır.  
  
> [!NOTE]
>  Bir çağrı içinde bir temsilci kullandığınızda, ortak dil çalışma zamanı bu çağrı süresi boyunca toplanan atık olarak temsilci korur. Yönetilmeyen işlev çağrısı tamamlandıktan sonra kullanmak için temsilci depoluyorsa, temsilci ile yönetilmeyen işlev tamamlanana kadar ancak el ile çöp toplama önlemeniz gerekir. Daha fazla bilgi için [HandleRef örneği](https://msdn.microsoft.com/library/ab23b04e-1d53-4ec7-b27a-e892d9298959(v=vs.100)) ve [GCHandle örneği](https://msdn.microsoft.com/library/6acce798-0385-4ded-a790-77da842c113f(v=vs.100)).  
  
 Geri çağırma örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
-   **TestCallBack** Pinvokelib.DLL'den dışarı.  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   **TestCallBack2** Pinvokelib.DLL'den dışarı.  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) daha önce listelenen işlevlerin için bir uygulama içeren özel bir yönetilmeyen kitaplıktır.  
  
 Bu örnekte `LibWrap` sınıfı için yönetilen prototipleri içeren `TestCallBack` ve `TestCallBack2` yöntemleri. Her iki yöntem de bir temsilci, bir parametre olarak bir geri çağırma işlevine geçirin. Metot temsilcisinin imzası başvurduğu metodun imzası eşleşmesi gerekir. Örneğin, `FPtr` ve `FPtr2` temsilciler sahip aynı imza `DoSomething` ve `DoSomething2` yöntemleri.  
  
## <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çeşitli sıralama örnekleri](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
- [Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
