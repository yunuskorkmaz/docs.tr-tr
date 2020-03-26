---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249506"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="b9f32-102">Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b9f32-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="b9f32-103">Değer türleri ve yapıları geçersiz ilan edilebilir.</span><span class="sxs-lookup"><span data-stu-id="b9f32-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="b9f32-104">Ancak, geçersiz bildirimi tür çıkarımlarıyla birlikte kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b9f32-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="b9f32-105">Aşağıdaki örnekler bu hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="b9f32-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="b9f32-106">**Hata Kimliği:** BC36629</span><span class="sxs-lookup"><span data-stu-id="b9f32-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9f32-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b9f32-107">To correct this error</span></span>  
  
- <span data-ttu-id="b9f32-108">Değişkeni `As` nullable değer türü olarak bildirmek için bir yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="b9f32-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f32-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9f32-109">See also</span></span>

- [<span data-ttu-id="b9f32-110">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="b9f32-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="b9f32-111">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9f32-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
