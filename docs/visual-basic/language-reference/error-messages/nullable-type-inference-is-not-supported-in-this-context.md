---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 7dffc5233656257cd892f573a2f8b9f91d781c21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611897"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="2ff8b-102">Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2ff8b-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="2ff8b-103">Değer türleri ve yapıları boş değer atanabilir bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2ff8b-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="2ff8b-104">Ancak, boş değer atanabilir bildirimi tür çıkarımı birlikte kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2ff8b-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="2ff8b-105">Aşağıdaki örnekler, bu hataya neden.</span><span class="sxs-lookup"><span data-stu-id="2ff8b-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="2ff8b-106">**Hata Kimliği:** BC36629</span><span class="sxs-lookup"><span data-stu-id="2ff8b-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ff8b-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2ff8b-107">To correct this error</span></span>  
  
-   <span data-ttu-id="2ff8b-108">Kullanım bir `As` olarak boş değer atanabilir bir değişken bildirmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="2ff8b-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff8b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ff8b-109">See also</span></span>
- [<span data-ttu-id="2ff8b-110">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="2ff8b-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="2ff8b-111">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="2ff8b-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
