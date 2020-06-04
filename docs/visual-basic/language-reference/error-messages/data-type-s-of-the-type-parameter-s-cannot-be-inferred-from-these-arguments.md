---
title: Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor
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
ms.openlocfilehash: b278dcc10a8a4e9e67aacdb16dca2588d2ebd0f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409796"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="8e64e-102">Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor</span><span class="sxs-lookup"><span data-stu-id="8e64e-102">Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>

<span data-ttu-id="8e64e-103">Tür parametrelerinin veri türleri bu bağımsız değişkenlerden çıkarılamıyor.</span><span class="sxs-lookup"><span data-stu-id="8e64e-103">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="8e64e-104">Veri türlerinin açıkça belirtilmesi bu hatayı düzeltebilir.</span><span class="sxs-lookup"><span data-stu-id="8e64e-104">Specifying the data type(s) explicitly might correct this error.</span></span>

<span data-ttu-id="8e64e-105">Aşırı yükleme çözümlemesi başarısız olduğunda bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="8e64e-105">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="8e64e-106">Belirli bir aşırı yükleme adayını neden ortadan kaldırmadığını belirten bir alt ileti olarak gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="8e64e-106">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="8e64e-107">Hata mesajı, derleyicinin tür çıkarımı için veri türlerini bulmak için tür çıkarımı kullanamadığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8e64e-107">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="8e64e-108">Bağımsız değişkenlerin belirtilmesi bir seçenek değil (örneğin, sorgu ifadelerinde sorgu işleçleri için), ikinci tümce olmadan hata iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8e64e-108">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>

<span data-ttu-id="8e64e-109">Aşağıdaki kod hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e64e-109">The following code demonstrates the error.</span></span>

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

<span data-ttu-id="8e64e-110">**Hata kimliği:** BC36647 ve BC36644</span><span class="sxs-lookup"><span data-stu-id="8e64e-110">**Error ID:** BC36647 and BC36644</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8e64e-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8e64e-111">To correct this error</span></span>

<span data-ttu-id="8e64e-112">Tür çıkarımı güvenmek yerine tür parametresi veya parametreleri için bir veri türü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e64e-112">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e64e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e64e-113">See also</span></span>

- [<span data-ttu-id="8e64e-114">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8e64e-114">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="8e64e-115">Visual Basic'de Genel Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8e64e-115">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="8e64e-116">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="8e64e-116">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
