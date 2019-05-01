---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 9f7f878649d8b96f050b56d5b878eb3d67e027ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918228"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="764fb-102">Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="764fb-102">Nullable type inference is not supported in this context</span></span>
<span data-ttu-id="764fb-103">Değer türleri ve yapıları boş değer atanabilir bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="764fb-103">Value types and structures can be declared nullable.</span></span>  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 <span data-ttu-id="764fb-104">Ancak, boş değer atanabilir bildirimi tür çıkarımı birlikte kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="764fb-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="764fb-105">Aşağıdaki örnekler, bu hataya neden.</span><span class="sxs-lookup"><span data-stu-id="764fb-105">The following examples cause this error.</span></span>  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 <span data-ttu-id="764fb-106">**Hata Kimliği:** BC36629</span><span class="sxs-lookup"><span data-stu-id="764fb-106">**Error ID:** BC36629</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="764fb-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="764fb-107">To correct this error</span></span>  
  
- <span data-ttu-id="764fb-108">Kullanım bir `As` olarak boş değer atanabilir bir değişken bildirmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="764fb-108">Use an `As` clause to declare the variable as nullable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="764fb-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="764fb-109">See also</span></span>

- [<span data-ttu-id="764fb-110">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="764fb-110">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="764fb-111">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="764fb-111">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
