---
title: <see> C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 995b67362bccbc3527f44e5a1d6b659f330e3afd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711720"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="7dd26-102">\<bkz. >C# (Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7dd26-102">\<see> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="7dd26-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7dd26-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dd26-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7dd26-104">Parameters</span></span>  
 <span data-ttu-id="7dd26-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="7dd26-105">cref = " `member`"</span></span>  
 <span data-ttu-id="7dd26-106">Geçerli derleme ortamından çağrılabilen bir üyeye veya alana başvuru.</span><span class="sxs-lookup"><span data-stu-id="7dd26-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="7dd26-107">Derleyici verilen kod öğesinin var olduğunu denetler ve çıkış XML dosyasında öğe adına `member` geçirir.</span><span class="sxs-lookup"><span data-stu-id="7dd26-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="7dd26-108">*Üyeyi* çift tırnak işareti ("") içine koyun.</span><span class="sxs-lookup"><span data-stu-id="7dd26-108">Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dd26-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7dd26-109">Remarks</span></span>  
 <span data-ttu-id="7dd26-110">\<bkz. > etiketi, metnin içinden bir bağlantı belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7dd26-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="7dd26-111">Metnin Ayrıca See de bir bölümüne yerleştirilmesi gerektiğini belirtmek için [\<see>](./seealso.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7dd26-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="7dd26-112">Kod öğeleri için belge sayfalarına iç köprüler oluşturmak üzere [cref özniteliğini](./cref-attribute.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7dd26-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="7dd26-113">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../language-reference/compiler-options/doc-compiler-option.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="7dd26-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="7dd26-114">Aşağıdaki örnek bir Özet bölümü içinde bir \<> etiketini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7dd26-114">The following example shows a \<see> tag within a summary section.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]  
  
## <a name="see-also"></a><span data-ttu-id="7dd26-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd26-115">See also</span></span>

- [<span data-ttu-id="7dd26-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7dd26-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7dd26-117">Belge Açıklamaları için Önerilen Etiketler</span><span class="sxs-lookup"><span data-stu-id="7dd26-117">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
