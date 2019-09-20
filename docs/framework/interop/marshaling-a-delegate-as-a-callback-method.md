---
title: Geri Çağırma Yöntemi Olarak Bir Temsilci Hazırlama
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
ms.openlocfilehash: 0e2289b3c12c7c83a39f1ad8d5a1365349ca6442
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151804"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>Geri Çağırma Yöntemi Olarak Bir Temsilci Hazırlama
Bu örnek, işlev işaretçileri bekleyen yönetilmeyen bir işleve temsilcilerin nasıl geçirileceğini gösterir. Bir temsilci, bir yönteme başvuru tutan ve tür kullanımı uyumlu işlev işaretçisine veya geri çağırma işlevine eşdeğer olan bir sınıftır.

> [!NOTE]
> Bir çağrı içinde bir temsilci kullandığınızda, ortak dil çalışma zamanı, bu çağrının süresi boyunca temsilciyi atık olarak toplanmaya karşı korur. Ancak, yönetilmeyen işlev çağrı tamamlandıktan sonra kullanmak üzere temsilciyi depoluyorsa, yönetilmeyen işlev temsilciyle bitene kadar çöp toplamayı el ile engellemeniz gerekir. Daha fazla bilgi için, bkz. [HandleRef örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) ve [GCHandle örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).

Geri çağırma örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:

- `TestCallBack`PInvokeLib. dll dosyasından verildi.

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- `TestCallBack2`PInvokeLib. dll dosyasından verildi.

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

[PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , daha önce listelenen işlevler için bir uygulama içeren özel bir yönetilmeyen kitaplıktır.

Bu örnekte, `NativeMethods` sınıfı `TestCallBack` ve `TestCallBack2` yöntemleri için yönetilen prototürler içerir. Her iki yöntem de bir çağrı işlevine parametre olarak bir temsilci iletir. Temsilcinin imzası, başvurduğu yöntemin imzasıyla aynı olmalıdır. Örneğin, `FPtr` ve `FPtr2` temsilcilerin `DoSomething` ve `DoSomething2` yöntemleriyle aynı olan imzaları vardır.

## <a name="declaring-prototypes"></a>Prototipleri Bildirme
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a>İşlevleri Çağırma
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a>Ayrıca bkz.

- [Çeşitli sıralama örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
- [Platform çağırma veri türleri](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
