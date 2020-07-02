---
title: Farklı Dizi Türlerini Hazırlama
description: Değer veya başvuruya göre tamsayılar, değere göre 2 boyutlu tamsayılar, değere göre dizeler ve tamsayı veya dizeler içeren yapılar gibi farklı dizi türlerini sıralama.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
ms.openlocfilehash: f1473c7917189f0b36c96b2adcf20005c5fd6b48
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621502"
---
# <a name="marshaling-different-types-of-arrays"></a>Farklı Dizi Türlerini Hazırlama
Dizi, aynı türde bir veya daha fazla öğe içeren Yönetilen koddaki bir başvuru türüdür. Diziler başvuru türleri olsa da, yönetilmeyen işlevlere parametre olarak geçirilir. Bu davranış, yönetilen dizilerin ın/out parametreleri gibi yönetilen nesnelere geçirilme yöntemi ile tutarlı değildir. Daha fazla bilgi için bkz. [kopyalama ve sabitleme](copying-and-pinning.md).  
  
 Aşağıdaki tabloda diziler için sıralama seçenekleri listelenmekte ve kullanımları açıklanmaktadır.  
  
|Dizi|Açıklama|  
|-----------|-----------------|  
|Değere göre tamsayılar.|Bir tamsayılar dizisini ın parametresi olarak geçirir.|  
|Başvuruya göre tamsayılar.|Bir tamsayı dizisini bir ın/out parametresi olarak geçirir.|  
|Değere göre tamsayılar (iki boyutlu).|Bir tamsayı matrisini bir ın parametresi olarak geçirir.|  
|Değere göre dizeler.|Bir dize dizisini ın parametresi olarak geçirir.|  
|, Tamsayılar içeren yapılar.|As parametresi olarak tamsayılar içeren bir yapı dizisini geçirir.|  
|Dizeleri olan yapılar.|Yalnızca dizeleri içeren bir yapı dizisini bir ın/out parametresi olarak geçirir. Dizi üyeleri değiştirilebilir.|  
  
## <a name="example"></a>Örnek  
 Bu örnek, aşağıdaki dizi türlerin nasıl geçirileceğini gösterir:  
  
- Değere göre tamsayılar dizisi.  
  
- Başvuruya göre tamsayılar dizisi, yeniden boyutlandırılabilir.  
  
- Değere göre tamsayılar için çok boyutlu dizi (matris).  
  
- Değere göre dizeler dizisi.  
  
- Tamsayılarla yapıların dizisi.  
  
- Dizeler içeren yapıların dizisi.  
  
 Bir dizi başvuruya göre açıkça sıralanmamışsa, varsayılan davranış diziyi bir ın parametresi olarak sıraladığında. <xref:System.Runtime.InteropServices.InAttribute>Ve özniteliklerini açıkça uygulayarak bu davranışı değiştirebilirsiniz <xref:System.Runtime.InteropServices.OutAttribute> .  
  
 Diziler örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
- PinvokeLib.dll 'den alınan **Testarrayofi** .  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- PinvokeLib.dll 'den dışarıya gelen **Testrefarrayoftri** .  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- PinvokeLib.dll 'den dışarıya gelen **Testmatrixoflitre** .  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- **TestArrayOfStrings** PinvokeLib.dll 'dan verildi.  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- PinvokeLib.dll 'den dışarıya gelen **Testarrayofyapılar** .  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- **TestArrayOfStructs2** PinvokeLib.dll dışarıya verildi.  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenen işlevler ve iki yapı değişkeni, **myPoint** ve **MyPerson**için uygulamalar içeren özel bir yönetilmeyen kitaplıktır. Yapılar aşağıdaki öğeleri içerir:  
  
```cpp
typedef struct _MYPOINT  
{  
   int x;
   int y;
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;
   char* last;
} MYPERSON;  
```  
  
 Bu örnekte, `MyPoint` ve `MyPerson` yapıları gömülü türler içerir. <xref:System.Runtime.InteropServices.StructLayoutAttribute>Özniteliği, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak üzere ayarlanır.  
  
 `NativeMethods`Sınıfı, sınıfı tarafından çağrılan bir yöntemler kümesi içerir `App` . Dizileri geçirme hakkında ayrıntılı bilgi için aşağıdaki örnekteki açıklamalara bakın. Başvuru türü olan bir dizi, varsayılan olarak bir ın parametresi olarak geçirilir. Çağıranın sonuçları alması için, **InAttribute** ve **OutAttribute** 'un, diziyi içeren bağımsız değişkene açıkça uygulanması gerekir.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Platform çağırma veri türleri](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
