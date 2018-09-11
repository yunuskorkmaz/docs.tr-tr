---
title: '&lt;typeparam&gt; (C# programlama Kılavuzu)'
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: ec19060008c1c06c54c89dbddee7d24001bcdebc
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44336660"
---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="2eb9c-102">&lt;typeparam&gt; (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2eb9c-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="2eb9c-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2eb9c-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2eb9c-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2eb9c-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2eb9c-105">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="2eb9c-105">The name of the type parameter.</span></span> <span data-ttu-id="2eb9c-106">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="2eb9c-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="2eb9c-107">Tür parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="2eb9c-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2eb9c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2eb9c-108">Remarks</span></span>  
 <span data-ttu-id="2eb9c-109">`<typeparam>` Etiketi genel bir tür veya yöntem bildirimi için açıklama açıklayan bir tür parametresi için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2eb9c-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="2eb9c-110">Genel tür veya yöntemin her tür parametresi için bir etiket ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2eb9c-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="2eb9c-111">Daha fazla bilgi için [genel türler](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="2eb9c-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="2eb9c-112">Metni `<typeparam>` etiketi IntelliSense içinde gösterilecek [nesne tarayıcı penceresi](https://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) kod açıklaması web rapor.</span><span class="sxs-lookup"><span data-stu-id="2eb9c-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](https://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="2eb9c-113">Derleme [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="2eb9c-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2eb9c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="2eb9c-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2eb9c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2eb9c-115">See Also</span></span>

- [<span data-ttu-id="2eb9c-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2eb9c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2eb9c-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2eb9c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2eb9c-118">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="2eb9c-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
