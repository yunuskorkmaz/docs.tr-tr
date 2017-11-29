---
title: Derleme (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef4434f0bc520abfc621567fc68e0b8bcfd6e381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="81f2e-102">Derleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81f2e-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="81f2e-103">Bir kaynak dosyasının başında bir öznitelik tüm derlemeye uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="81f2e-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81f2e-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81f2e-104">Remarks</span></span>  
 <span data-ttu-id="81f2e-105">Çok sayıda özniteliği bir sınıf veya özellik gibi tek bir programlama öğe ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="81f2e-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="81f2e-106">Köşeli parantez içinde öznitelik blok ekleyerek bu tür bir öznitelik geçerli (`< >`), bildirim deyiminin için doğrudan.</span><span class="sxs-lookup"><span data-stu-id="81f2e-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="81f2e-107">Bir öznitelik değil yalnızca aşağıdaki öğesine, ancak tüm derleme ilgiliyse, öznitelik blok kaynak dosyasının başında yerleştirin ve öznitelik tanımlamak `Assembly` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="81f2e-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="81f2e-108">Geçerli derleme modülü geçerliyse, kullandığınız [Modülü](../../../visual-basic/language-reference/modifiers/module-keyword.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="81f2e-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="81f2e-109">Bir öznitelik AssemblyInfo.vb dosyasındaki bir derlemenin, bu durumda, bir öznitelik blok ana kaynak kodu dosyanızda kullanmak zorunda değil de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81f2e-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f2e-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81f2e-110">See Also</span></span>  
 [<span data-ttu-id="81f2e-111">Modül \<anahtar sözcüğü ></span><span class="sxs-lookup"><span data-stu-id="81f2e-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="81f2e-112">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="81f2e-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

