---
description: 'Şu konuda daha fazla bilgi edinin: BC36629: Nullable tür çıkarımı bu bağlamda desteklenmiyor'
title: Bu bağlamda boş değerler atanabilen tür çıkarma desteklenmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 915f964d55068f39b0468e2c47cc6e5538be1a6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795631"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="b91c9-103">BC36629: Nullable tür çıkarımı bu bağlamda desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="b91c9-103">BC36629: Nullable type inference is not supported in this context</span></span>

<span data-ttu-id="b91c9-104">Değer türleri ve yapıları null yapılabilir olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="b91c9-104">Value types and structures can be declared nullable.</span></span>

```vb
Dim a? As Integer
Dim b As Integer?
```

 <span data-ttu-id="b91c9-105">Ancak, null yapılabilir bildirimini tür çıkarımı ile birlikte kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b91c9-105">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="b91c9-106">Aşağıdaki örnekler bu hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="b91c9-106">The following examples cause this error.</span></span>

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 <span data-ttu-id="b91c9-107">**Hata kimliği:** BC36629</span><span class="sxs-lookup"><span data-stu-id="b91c9-107">**Error ID:** BC36629</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b91c9-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b91c9-108">To correct this error</span></span>

- <span data-ttu-id="b91c9-109">`As`Değişkeni null yapılabilir bir değer türü olarak bildirmek için bir yan tümce kullanın.</span><span class="sxs-lookup"><span data-stu-id="b91c9-109">Use an `As` clause to declare the variable as a nullable value type.</span></span>

## <a name="see-also"></a><span data-ttu-id="b91c9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b91c9-110">See also</span></span>

- [<span data-ttu-id="b91c9-111">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="b91c9-111">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="b91c9-112">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b91c9-112">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
