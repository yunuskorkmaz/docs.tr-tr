---
title: Farklı Dizi Türlerini Sıralama
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
ms.openlocfilehash: b0c71284fbc925aa9bb10a8bf68cef581f78d7f4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50088760"
---
# <a name="marshaling-different-types-of-arrays"></a>Farklı Dizi Türlerini Hazırlama
Bir dizi aynı türden bir veya daha fazla öğe içeriyor, yönetilen kodda bir başvuru türüdür. Diziler başvuru türleri olsa da, olduğu gibi parametreleri yönetilmeyen bir işleve geçirilir. Bu davranış, In/Out parametreleri olan yönetilen nesnelere, yönetilen diziler geçirilen yolu ile tutarsız. Ek ayrıntılar için bkz. [kopyalama ve sabitleme](copying-and-pinning.md).  
  
 Aşağıdaki tabloda, dizileri sıralama seçeneklerini listeler ve bunların kullanımını açıklar.  
  
|Dizi|Açıklama|  
|-----------|-----------------|  
|Değere göre tamsayılar.|Tamsayı dizisi, bir giriş parametresi olarak geçirir.|  
|Başvuruya göre tamsayılar.|Tamsayı dizisi bir ın/Out parametresi olarak geçirir.|  
|Tamsayılar değeriyle (iki boyutlu).|Matris tamsayı bir giriş parametresi olarak geçirir.|  
|Değere göre dizeleri.|Dizelerden oluşan bir dizi bir giriş parametresi olarak geçirir.|  
|Yapıları ile tamsayı.|Bir dizi bir giriş parametresi olarak tamsayılar içeren yapılarını geçirir.|  
|Yapıları dizeler.|Bir dizi yalnızca tamsayı içeren bir ın/Out parametresi olarak yapılarını geçirir. Dizi üyelerinin değiştirilebilir.|  
  
## <a name="example"></a>Örnek  
 Bu örnek, dizileri aşağıdaki türleri nasıl gösterir:  
  
-   Değer tamsayı dizisi.  
  
-   Yeniden boyutlandırılabilir başvuruya göre tamsayı dizisi.  
  
-   Tamsayı değerine göre çok boyutlu dizisi (matrix).  
  
-   Değer bir dize dizisi.  
  
-   Yapıları ile tamsayı dizisi.  
  
-   Yapıları dizeler dizisi.  
  
 Bir dizi başvuruya göre açıkça sıralanır sürece, varsayılan davranışı dizi bir giriş parametresi olarak sürekliliğe devreder. Uygulayarak bu davranışı değiştirebilirsiniz <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> açıkça öznitelikleri.  
  
 Diziler örneği, orijinal işlev bildirimleriyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
-   **TestArrayOfInts** Pinvokelib.DLL'den dışarı.  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   **TestRefArrayOfInts** Pinvokelib.DLL'den dışarı.  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   **TestMatrixOfInts** Pinvokelib.DLL'den dışarı.  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   **TestArrayOfStrings** Pinvokelib.DLL'den dışarı.  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   **TestArrayOfStructs** Pinvokelib.DLL'den dışarı.  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   **TestArrayOfStructs2** Pinvokelib.DLL'den dışarı.  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as6wyhwt(v=vs.100)) daha önce listelenen işlevlerin ve iki yapı değişkenleri için uygulamaları içeren özel bir yönetilmeyen kitaplıktır **MYPOINT** ve **MYPERSON**. Yapılar aşağıdaki öğeleri içerir:  
  
```  
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
  
 Bu örnekte `MyPoint` ve `MyPerson` yapıları katıştırılmış türleri içerir. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği, üyelerin bellekte sıralı olarak, göründükleri sırayla gözüktükleri ayarlanır.  
  
 `LibWrap` Sınıfı içeren bir dizi çağıran yöntem `App` sınıfı. Dizileri geçirme hakkında belirli bilgiler için aşağıdaki örnekte yer alan yorumlara bakın. Bir başvuru türü bir dizi varsayılan olarak bir giriş parametresi olarak geçirilir. Sonuçları almak çağırıcı için **InAttribute** ve **OutAttribute** diziyi içeren bir bağımsız değişken için açıkça uygulanmalıdır.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür dizilerini sıralama](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
