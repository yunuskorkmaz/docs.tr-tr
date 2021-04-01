---
ms.openlocfilehash: 83644b9205d650da68c910095dd1d22a14940c44
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "97366835"
---
### <a name="exclude-specific-symbols"></a><span data-ttu-id="5ab0d-101">Belirli sembolleri Dışla</span><span class="sxs-lookup"><span data-stu-id="5ab0d-101">Exclude specific symbols</span></span>

<span data-ttu-id="5ab0d-102">Tür ve yöntemler gibi belirli sembolleri analizden dışlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ab0d-102">You can exclude specific symbols, such as types and methods, from analysis.</span></span> <span data-ttu-id="5ab0d-103">Örneğin, kuralın adlı tür içindeki herhangi bir kodda çalıştırılmamalıdır `MyType` , aşağıdaki anahtar-değer çiftini projenizdeki bir *. editorconfig* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5ab0d-103">For example, to specify that the rule should not run on any code within types named `MyType`, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType
```

<span data-ttu-id="5ab0d-104">Seçenek değerindeki izin verilen sembol adı biçimleri (ile ayrılmış `|` ):</span><span class="sxs-lookup"><span data-stu-id="5ab0d-104">Allowed symbol name formats in the option value (separated by `|`):</span></span>

- <span data-ttu-id="5ab0d-105">Yalnızca sembol adı (kapsayan tür veya ad alanından bağımsız olarak ada sahip tüm sembolleri içerir).</span><span class="sxs-lookup"><span data-stu-id="5ab0d-105">Symbol name only (includes all symbols with the name, regardless of the containing type or namespace).</span></span>
- <span data-ttu-id="5ab0d-106">Simgenin [belge kimliği biçimindeki](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings)tam adlar.</span><span class="sxs-lookup"><span data-stu-id="5ab0d-106">Fully qualified names in the symbol's [documentation ID format](../../docs/csharp/programming-guide/xmldoc/processing-the-xml-file.md#id-strings).</span></span> <span data-ttu-id="5ab0d-107">Her sembol adı, metotlar için, `M:` `T:` türler için ve ad alanları gibi bir sembol türü ön eki gerektirir `N:` .</span><span class="sxs-lookup"><span data-stu-id="5ab0d-107">Each symbol name requires a symbol-kind prefix, such as `M:` for methods, `T:` for types, and `N:` for namespaces.</span></span>
- <span data-ttu-id="5ab0d-108">`.ctor` oluşturucular ve `.cctor` statik oluşturucular için.</span><span class="sxs-lookup"><span data-stu-id="5ab0d-108">`.ctor` for constructors and `.cctor` for static constructors.</span></span>

<span data-ttu-id="5ab0d-109">Örnekler:</span><span class="sxs-lookup"><span data-stu-id="5ab0d-109">Examples:</span></span>

| <span data-ttu-id="5ab0d-110">Seçenek değeri</span><span class="sxs-lookup"><span data-stu-id="5ab0d-110">Option Value</span></span> | <span data-ttu-id="5ab0d-111">Özet</span><span class="sxs-lookup"><span data-stu-id="5ab0d-111">Summary</span></span> |
| --- | --- |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType` | <span data-ttu-id="5ab0d-112">Adlı tüm simgeleri eşleştirir `MyType` .</span><span class="sxs-lookup"><span data-stu-id="5ab0d-112">Matches all symbols named `MyType`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = MyType1|MyType2` | <span data-ttu-id="5ab0d-113">Ya da adlı tüm sembolleri `MyType1` eşler `MyType2` .</span><span class="sxs-lookup"><span data-stu-id="5ab0d-113">Matches all symbols named either `MyType1` or `MyType2`.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS.MyType.MyMethod(ParamType)` | <span data-ttu-id="5ab0d-114">`MyMethod`Belirtilen tam imzaya sahip belirli bir yöntemle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5ab0d-114">Matches specific method `MyMethod` with the specified fully qualified signature.</span></span> |
|`dotnet_code_quality.CAXXXX.excluded_symbol_names = M:NS1.MyType1.MyMethod1(ParamType)|M:NS2.MyType2.MyMethod2(ParamType)` | <span data-ttu-id="5ab0d-115">Belirli yöntemlerle `MyMethod1` ve `MyMethod2` ilgili tam imzalarla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5ab0d-115">Matches specific methods `MyMethod1` and `MyMethod2` with the respective fully qualified signatures.</span></span> |
