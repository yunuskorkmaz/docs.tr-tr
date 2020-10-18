---
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 610d2dc427d882c412b87eb67f021a8a86025f25
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159936"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="ed4dd-102">BC36629: Nullable tür çıkarımı bu bağlamda desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="ed4dd-102">BC36629: Nullable type inference is not supported in this context</span></span>

<span data-ttu-id="ed4dd-103">Değer türleri ve yapıları null yapılabilir olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="ed4dd-103">Value types and structures can be declared nullable.</span></span>

```vb
Dim a? As Integer
Dim b As Integer?
```

 <span data-ttu-id="ed4dd-104">Ancak, null yapılabilir bildirimini tür çıkarımı ile birlikte kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="ed4dd-104">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="ed4dd-105">Aşağıdaki örnekler bu hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="ed4dd-105">The following examples cause this error.</span></span>

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 <span data-ttu-id="ed4dd-106">**Hata kimliği:** BC36629</span><span class="sxs-lookup"><span data-stu-id="ed4dd-106">**Error ID:** BC36629</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ed4dd-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ed4dd-107">To correct this error</span></span>

- <span data-ttu-id="ed4dd-108">`As`Değişkeni null yapılabilir bir değer türü olarak bildirmek için bir yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed4dd-108">Use an `As` clause to declare the variable as a nullable value type.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed4dd-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed4dd-109">See also</span></span>

- [<span data-ttu-id="ed4dd-110">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="ed4dd-110">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="ed4dd-111">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed4dd-111">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
