---
title: Farklı Dizi Türlerini Sıralama
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 62958f1656dfbfcb45356378161090b8271b6b83
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="marshaling-different-types-of-arrays"></a>Farklı Dizi Türlerini Hazırlama
Bir dizi aynı türde bir veya daha fazla öğe içeriyor, yönetilen kodda bir başvuru türüdür. Diziler başvuru türleri olsa da, bunlar parametreler olduğu gibi yönetilmeyen işlevlerle iletilir. Bu davranış, olan olarak In/Out parametreleri yönetilen diziler yönetilen nesnelere geçirilir şekilde tutmuyor. Daha fazla bilgi için bkz: [kopyalama ve sabitleme](copying-and-pinning.md).  
  
 Aşağıdaki tabloda dizileri sıralama seçeneklerini listeler ve bunların kullanım açıklar.  
  
|Dizi|Açıklama|  
|-----------|-----------------|  
|Değere göre tamsayılar.|Dizisi bir giriş parametresi olarak geçirir.|  
|Başvuruya göre tamsayılar.|Dizisi bir giriş/çıkış parametre olarak geçirir.|  
|Tamsayılar değerle (iki boyutlu).|Tamsayıların bir matris bir giriş parametresi olarak geçirir.|  
|Değere göre dizeleri.|Dize dizisi bir giriş parametresi olarak geçirir.|  
|Yapıları tamsayılı.|Bir dizi tamsayılar bir giriş parametresi olarak içeren yapılarını geçirir.|  
|Dizeler yapıları.|Bir giriş/çıkış parametresi olarak yalnızca tamsayı içeren yapılarını dizisi geçirir. Dizi üyelerinin değiştirilebilir.|  
  
## <a name="example"></a>Örnek  
 Bu örnek, dizi aşağıdaki türlerini geçirmek gösterilmiştir:  
  
-   Değere göre dizisi yanıtlar.  
  
-   Yeniden boyutlandırılabilir başvuruya göre dizisi yanıtlar.  
  
-   Çok boyutlu dizisi (Matris) değeri.  
  
-   Değere göre bir dizeler dizisi.  
  
-   Yapıları tamsayılı dizisi.  
  
-   Yapıları dizeler dizisi.  
  
 Bir dizi açıkça başvuruya göre sıralanmış sürece, varsayılan davranışı dizi bir giriş parametresi olarak sıralar. Uygulayarak bu davranışı değiştirebilirsiniz <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> açıkça öznitelikleri.  
  
 Diziler örneği kendi özgün işlevi bildirimiyle gösterilen aşağıdaki yönetilmeyen işlevleri kullanır:  
  
-   **TestArrayOfInts** PinvokeLib.dll dışarı.  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   **TestRefArrayOfInts** PinvokeLib.dll dışarı.  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   **TestMatrixOfInts** PinvokeLib.dll dışarı.  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   **TestArrayOfStrings** PinvokeLib.dll dışarı.  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   **TestArrayOfStructs** PinvokeLib.dll dışarı.  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   **TestArrayOfStructs2** PinvokeLib.dll dışarı.  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 [PinvokeLib.dll](https://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614(v=vs.100)) daha önce listelenen işlevler ve iki yapı değişkenleri için uygulamaları içeren özel bir yönetilmeyen kitaplık **MYPOINT** ve **MYPERSON**. Yapıları aşağıdaki öğeleri içerir:  
  
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
  
 Bu örnekte `MyPoint` ve `MyPerson` yapıları katıştırılmış türler içerir. <xref:System.Runtime.InteropServices.StructLayoutAttribute> Özniteliği ayarlanmış üyeleri bellekte ardışık olarak göründükleri sırada düzenlenmiş emin olun.  
  
 `LibWrap` Sınıfı içeren bir dizi yöntem tarafından çağrılır `App` sınıfı. Dizileri geçirme hakkında belirli Ayrıntılar için aşağıdaki örnek yer alan yorumlara bakın. Bir başvuru türü olan bir dizi varsayılan olarak bir giriş parametresi olarak geçirilir. Çağıran sonuçlarını almak için **InAttribute** ve **OutAttribute** dizi içeren bağımsız değişkeni açıkça uygulanmış olması gerekir.  
  
### <a name="declaring-prototypes"></a>Prototipleri Bildirme  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a>İşlevleri Çağırma  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Türlerin dizileri sıralama](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Yönetilen Kodda Prototipler Oluşturma](creating-prototypes-in-managed-code.md)
