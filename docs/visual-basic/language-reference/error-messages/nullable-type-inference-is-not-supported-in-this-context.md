---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409393"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="3fff4-102">Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="3fff4-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="3fff4-103">Değer türleri ve yapıları null yapılabilir olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="3fff4-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="3fff4-104">Ancak, null yapılabilir bildirimini tür çıkarımı ile birlikte kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3fff4-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="3fff4-105">Aşağıdaki örnekler bu hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="3fff4-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="3fff4-106">**Hata kimliği:** BC36629</span><span class="sxs-lookup"><span data-stu-id="3fff4-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3fff4-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3fff4-107">To correct this error</span></span>  
  
- <span data-ttu-id="3fff4-108">`As`Değişkeni null yapılabilir bir değer türü olarak bildirmek için bir yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="3fff4-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fff4-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fff4-109">See also</span></span>

- [<span data-ttu-id="3fff4-110">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="3fff4-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="3fff4-111">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3fff4-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
