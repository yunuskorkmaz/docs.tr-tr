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
ms.openlocfilehash: 66c7ba5989952edb55f21aab960ad7395a92ae0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181361"
---
# <a name="marshaling-different-types-of-arrays"></a>Farklı Dizi Türlerini Hazırlama
Dizi, yönetilen kodda aynı türden bir veya daha fazla öğe içeren bir başvuru türüdür. Diziler başvuru türleri olsa da, yönetilmeyen işlevlere parametreler olarak geçirilirler. Bu davranış, yönetilen dizilerin yönetilen nesnelere geçirildiği ve In/Out parametreleri olarak geçirildiğiyle tutarsızdır. Ek ayrıntılar için [bkz.](copying-and-pinning.md)  
  
 Aşağıdaki tabloda diziler için mareşal seçenekleri listelanır ve bunların kullanımını açıklar.  
  
|Dizi|Açıklama|  
|-----------|-----------------|  
|Değere göre tümsadanların.|Bir in parametresi olarak bir dizi tümseci geçirir.|  
|Referans olarak tümsadanların.|Bir dizi integer'ı Giriş/Çıkış parametresi olarak geçirir.|  
|Değere göre tümsaderlerin (iki boyutlu).|Tamsayılar matrisini In parametresi olarak geçirir.|  
|Dizilerin değerine göre.|Bir dizi dizeyi In parametresi olarak geçirir.|  
|İntegerli yapıların.|In parametresi olarak, içinde hiçsesayı içeren bir dizi yapıyı geçirir.|  
|Dizeleri olan yapıların.|Yalnızca Giriş/Çıkış parametresi olarak dizeleri içeren bir dizi yapıyı geçirir. Dizinin üyeleri değiştirilebilir.|  
  
## <a name="example"></a>Örnek  
 Bu örnek, aşağıdaki dizi türlerinin nasıl geçirilen gösteriş gösterir:  
  
- Değere göre tümerler dizisi.  
  
- Yeniden boyutlandırılabilen başvuru yaylaları dizisi.  
  
- Değere göre çok boyutlu dizi (matris).  
  
- Değere göre dize dizisi.  
  
- Tümsegeriçeren yapıların dizisi.  
  
- Dizeleri ile yapıların dizi.  
  
 Bir dizi açıkça başvuru tarafından marshaled sürece, varsayılan davranış bir In parametresi olarak dizi marshals. Bu davranışı <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> öznitelikleri açıkça uygulayarak değiştirebilirsiniz.  
  
 Diziler örneği, özgün işlev bildirimiile gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
- PinvokeLib.dll'den ihraç edilen **TestArrayOfInts.**  
  
    ```cpp
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
- **TestRefArrayOfInts** PinvokeLib.dll ihraç.  
  
    ```cpp
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
- PinvokeLib.dll'den ihraç edilen **TestMatrixOfInts.**  
  
    ```cpp
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
- PinvokeLib.dll'den dışa aktarılan **TestArrayOfStrings.**  
  
    ```cpp
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
- PinvokeLib.dll'den ihraç edilen **TestArrayOfStructs.**  
  
    ```cpp
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
- **TestArrayOfStructs2** PinvokeLib.dll'den ihraç edildi.  
  
    ```cpp
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll,](marshaling-data-with-platform-invoke.md#pinvokelibdll) daha önce listelenen işlevler ve **MYPOINT** ve **MYPERSON**olmak üzere iki yapı değişkeni için uygulamalar içeren özel bir yönetilmeyen kitaplıktır. Yapılar aşağıdaki öğeleri içerir:  
  
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
  
 Bu örnekte, `MyPoint` `MyPerson` ve yapılar gömülü türleri içerir. Öznitelik, <xref:System.Runtime.InteropServices.StructLayoutAttribute> üyelerin göründükleri sırada, sırayla bellekte düzenlendiğinden emin olmak için ayarlanır.  
  
 Sınıf, `NativeMethods` `App` sınıf tarafından çağrılan bir dizi yöntem içerir. Geçen diziler hakkında özel ayrıntılar için aşağıdaki örnekteki yorumlara bakın. Başvuru türü olan bir dizi varsayılan olarak In parametresi olarak geçirilir. Arayanın sonuçları alabilmesi için, diziyi içeren bağımsız değişkene açık olarak **InAttribute** ve **OutAttribute** uygulanmalıdır.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Platform çağrıcı veri türleri](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
