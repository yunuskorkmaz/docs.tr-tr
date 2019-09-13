---
title: Farklı Dizi Türlerini Hazırlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 358c7f1a339fd473271574a4e97e201f5c15f871
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894173"
---
# <a name="marshaling-different-types-of-arrays"></a>Farklı Dizi Türlerini Hazırlama
Dizi, aynı türde bir veya daha fazla öğe içeren Yönetilen koddaki bir başvuru türüdür. Diziler başvuru türleri olsa da, yönetilmeyen işlevlere parametre olarak geçirilir. Bu davranış, yönetilen dizilerin ın/out parametreleri gibi yönetilen nesnelere geçirilme yöntemi ile tutarlı değildir. Daha fazla bilgi için bkz. [kopyalama ve sabitleme](copying-and-pinning.md).  
  
 Aşağıdaki tabloda diziler için sıralama seçenekleri listelenmekte ve kullanımları açıklanmaktadır.  
  
|Array|Açıklama|  
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
  
 Bir dizi başvuruya göre açıkça sıralanmamışsa, varsayılan davranış diziyi bir ın parametresi olarak sıraladığında. <xref:System.Runtime.InteropServices.InAttribute> Ve<xref:System.Runtime.InteropServices.OutAttribute> özniteliklerini açıkça uygulayarak bu davranışı değiştirebilirsiniz.  
  
 Diziler örneği, özgün işlev bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
- PInvokeLib. dll ' den alınan **Tebaşlangıçraylar** .  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- PInvokeLib. dll dosyasından **test edilmiş Testrefarray.**  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- PInvokeLib. dll dosyasından alınan **Testmatrixoflitre** .  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- **TestArrayOfStrings** , PInvokeLib. dll dosyasından verildi.  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- PInvokeLib. dll dosyasından aktarılmış **Testarrayofyapılar** .  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- **TestArrayOfStructs2** , PInvokeLib. dll dosyasından verildi.  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PInvokeLib. dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) , önceden listelenen işlevler ve iki yapı değişkeni, **myPoint** ve **MyPerson**için uygulamalar içeren özel bir yönetilmeyen kitaplıktır. Yapılar aşağıdaki öğeleri içerir:  
  
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
  
 Bu örnekte, `MyPoint` ve `MyPerson` yapıları gömülü türler içerir. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, üyelerin bellekte sırayla, göründükleri sırada düzenlendiğinden emin olmak üzere ayarlanır.  
  
 Sınıfı, `App` sınıfı tarafından çağrılan bir yöntemler kümesi içerir. `LibWrap` Dizileri geçirme hakkında ayrıntılı bilgi için aşağıdaki örnekteki açıklamalara bakın. Başvuru türü olan bir dizi, varsayılan olarak bir ın parametresi olarak geçirilir. Çağıranın sonuçları alması için, **InAttribute** ve **OutAttribute** 'un, diziyi içeren bağımsız değişkene açıkça uygulanması gerekir.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Platform çağırma veri türleri](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
