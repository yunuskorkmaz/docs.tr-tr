---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <param> (Visual Basic)'
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 94fe5e11d5846f7fa00eb73c1c4363990ae23b2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700302"
---
# <a name="param-visual-basic"></a><span data-ttu-id="66110-103">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66110-103">\<param> (Visual Basic)</span></span>

<span data-ttu-id="66110-104">Bir parametre adı ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66110-104">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66110-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66110-105">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="66110-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66110-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="66110-107">Bir yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="66110-107">The name of a method parameter.</span></span> <span data-ttu-id="66110-108">Adı çift tırnak işareti ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="66110-108">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="66110-109">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="66110-109">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66110-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66110-110">Remarks</span></span>  

 <span data-ttu-id="66110-111">`<param>`Yöntemi, yöntemin parametrelerinden birini açıklayacak bir yöntem bildirimine ilişkin açıklamada kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66110-111">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="66110-112">`<param>`Etiketin metni aşağıdaki konumlarda görünür:</span><span class="sxs-lookup"><span data-stu-id="66110-112">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="66110-113">IntelliSense parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="66110-113">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="66110-114">Daha fazla bilgi için bkz. [IntelliSense kullanma](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="66110-114">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="66110-115">Nesne Tarayıcısı.</span><span class="sxs-lookup"><span data-stu-id="66110-115">Object Browser.</span></span> <span data-ttu-id="66110-116">Daha fazla bilgi için bkz. [kod yapısını görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="66110-116">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="66110-117">Belge açıklamalarını bir dosyaya işlemek için [-doc](../../reference/command-line-compiler/doc.md) ile derleyin.</span><span class="sxs-lookup"><span data-stu-id="66110-117">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66110-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="66110-118">Example</span></span>  

 <span data-ttu-id="66110-119">Bu örnek, `<param>` parametresini anlatmak için etiketini kullanır `id` .</span><span class="sxs-lookup"><span data-stu-id="66110-119">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="66110-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66110-120">See also</span></span>

- [<span data-ttu-id="66110-121">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="66110-121">XML Comment Tags</span></span>](index.md)
