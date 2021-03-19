---
title: Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor
description: 'Şu konuda daha fazla bilgi edinin: BC36647 ve BC36644: tür parametrelerinin veri türleri bu bağımsız değişkenlerden çıkarılamıyor'
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 26b4358dc2059aaff0a6a72d1489216c854f79a6
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653679"
---
# <a name="bc36647-and-bc36644-data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="dadb8-103">BC36647 ve BC36644: tür parametrelerinin veri türleri bu bağımsız değişkenlerden çıkarılamıyor</span><span class="sxs-lookup"><span data-stu-id="dadb8-103">BC36647 and BC36644: Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>

<span data-ttu-id="dadb8-104">Tür parametrelerinin veri türleri bu bağımsız değişkenlerden çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="dadb8-104">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="dadb8-105">Veri türlerinin açıkça belirtilmesi bu hatayı düzeltebilir.</span><span class="sxs-lookup"><span data-stu-id="dadb8-105">Specifying the data type(s) explicitly might correct this error.</span></span>

<span data-ttu-id="dadb8-106">Aşırı yükleme çözümlemesi başarısız olduğunda bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="dadb8-106">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="dadb8-107">Belirli bir aşırı yükleme adayını neden ortadan kaldırmadığını belirten bir alt ileti olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="dadb8-107">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="dadb8-108">Hata mesajı, derleyicinin tür çıkarımı için veri türlerini bulmak için tür çıkarımı kullanamadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="dadb8-108">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="dadb8-109">Bağımsız değişkenlerin belirtilmesi bir seçenek değil (örneğin, sorgu ifadelerinde sorgu işleçleri için), ikinci tümce olmadan hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="dadb8-109">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>

<span data-ttu-id="dadb8-110">Aşağıdaki kod hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="dadb8-110">The following code demonstrates the error.</span></span>

```vb
Module Module1

    Sub Main()

        '' Not Valid.
        'OverloadedGenericMethod("Hello", "World")

    End Sub

    Sub OverloadedGenericMethod(Of T)(ByVal x As String,
                                      ByVal y As InterfaceExample(Of T))
    End Sub

    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,
                                         ByVal y As InterfaceExample(Of R))
    End Sub

End Module

Interface InterfaceExample(Of T)
End Interface
```

<span data-ttu-id="dadb8-111">**Hata kimliği:** BC36647 ve BC36644</span><span class="sxs-lookup"><span data-stu-id="dadb8-111">**Error ID:** BC36647 and BC36644</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="dadb8-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="dadb8-112">To correct this error</span></span>

<span data-ttu-id="dadb8-113">Tür çıkarımı güvenmek yerine tür parametresi veya parametreleri için bir veri türü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dadb8-113">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>

## <a name="see-also"></a><span data-ttu-id="dadb8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dadb8-114">See also</span></span>

- [<span data-ttu-id="dadb8-115">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="dadb8-115">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="dadb8-116">Visual Basic'de Genel Yordamlar</span><span class="sxs-lookup"><span data-stu-id="dadb8-116">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="dadb8-117">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="dadb8-117">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
