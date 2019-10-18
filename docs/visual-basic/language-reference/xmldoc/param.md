---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c62eab6b1fb1ba1cc7de83c12d7205cf0bbe46fa
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524724"
---
# <a name="param-visual-basic"></a><span data-ttu-id="3bd05-102">\<param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3bd05-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="3bd05-103">Bir parametre adı ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3bd05-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bd05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bd05-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bd05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bd05-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3bd05-106">Bir yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="3bd05-106">The name of a method parameter.</span></span> <span data-ttu-id="3bd05-107">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="3bd05-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="3bd05-108">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="3bd05-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bd05-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3bd05-109">Remarks</span></span>  
 <span data-ttu-id="3bd05-110">Metodun parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada `<param>` etiketinin kullanılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3bd05-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="3bd05-111">@No__t_0 etiketinin metni aşağıdaki konumlarda görünür:</span><span class="sxs-lookup"><span data-stu-id="3bd05-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="3bd05-112">IntelliSense parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="3bd05-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="3bd05-113">Daha fazla bilgi için bkz. [IntelliSense kullanma](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="3bd05-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="3bd05-114">Nesne Tarayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3bd05-114">Object Browser.</span></span> <span data-ttu-id="3bd05-115">Daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="3bd05-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="3bd05-116">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="3bd05-116">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bd05-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="3bd05-117">Example</span></span>  
 <span data-ttu-id="3bd05-118">Bu örnek, `id` parametresini anlatmak için `<param>` etiketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bd05-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3bd05-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bd05-119">See also</span></span>

- [<span data-ttu-id="3bd05-120">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="3bd05-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
