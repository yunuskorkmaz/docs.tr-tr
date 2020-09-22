---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 19300a928a59c7259f81b282bd28d9bdd447d76b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872625"
---
# <a name="param-visual-basic"></a><span data-ttu-id="257dd-101">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="257dd-101">\<param> (Visual Basic)</span></span>

<span data-ttu-id="257dd-102">Bir parametre adı ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="257dd-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="257dd-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="257dd-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="257dd-104">Parametreler</span><span class="sxs-lookup"><span data-stu-id="257dd-104">Parameters</span></span>  

 `name`  
 <span data-ttu-id="257dd-105">Bir yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="257dd-105">The name of a method parameter.</span></span> <span data-ttu-id="257dd-106">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="257dd-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="257dd-107">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="257dd-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="257dd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="257dd-108">Remarks</span></span>  

 <span data-ttu-id="257dd-109">`<param>`Yöntemi, yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="257dd-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="257dd-110">`<param>`Etiketin metni aşağıdaki konumlarda görünür:</span><span class="sxs-lookup"><span data-stu-id="257dd-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="257dd-111">IntelliSense parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="257dd-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="257dd-112">Daha fazla bilgi için bkz. [IntelliSense kullanma](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="257dd-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="257dd-113">Nesne Tarayıcısı.</span><span class="sxs-lookup"><span data-stu-id="257dd-113">Object Browser.</span></span> <span data-ttu-id="257dd-114">Daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="257dd-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="257dd-115">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="257dd-115">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="257dd-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="257dd-116">Example</span></span>  

 <span data-ttu-id="257dd-117">Bu örnek, `<param>` parametresini anlatmak için etiketini kullanır `id` .</span><span class="sxs-lookup"><span data-stu-id="257dd-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="257dd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="257dd-118">See also</span></span>

- [<span data-ttu-id="257dd-119">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="257dd-119">XML Comment Tags</span></span>](index.md)
