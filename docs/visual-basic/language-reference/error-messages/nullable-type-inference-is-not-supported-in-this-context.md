---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: ea531c7be676e940a263b019a66cc80cf280a772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593197"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="037c0-102">Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="037c0-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="037c0-103">Değer türleri ve yapıları boş değer atanabilir bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="037c0-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="037c0-104">Ancak, boş değer atanabilir bildirimi tür çıkarımı ile birlikte kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="037c0-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="037c0-105">Aşağıdaki örnekler, bu hataya neden.</span><span class="sxs-lookup"><span data-stu-id="037c0-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="037c0-106">**Hata Kimliği:** BC36629</span><span class="sxs-lookup"><span data-stu-id="037c0-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="037c0-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="037c0-107">To correct this error</span></span>  
  
-   <span data-ttu-id="037c0-108">Kullanım bir `As` değişkeni boş değer atanabilir olarak bildirmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="037c0-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="037c0-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="037c0-109">See Also</span></span>  
 [<span data-ttu-id="037c0-110">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="037c0-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="037c0-111">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="037c0-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
