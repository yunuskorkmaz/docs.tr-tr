---
title: Global bağlamsal anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 837245e31a9a795aa2f13cfc6c33fefb6402801d
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699666"
---
# <a name="global-c-reference"></a><span data-ttu-id="0ea7e-102">global (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0ea7e-102">global (C# Reference)</span></span>

<span data-ttu-id="0ea7e-103">`global` Önce söz konusu olduğunda bağlamsal anahtar sözcük [:: işleci](../operators/namespace-alias-qualifer.md), herhangi bir C# programı için varsayılan ad alanı ve aksi takdirde adlandırılmamış genel ad alanına başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="0ea7e-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="0ea7e-104">Daha fazla bilgi için [nasıl yapılır: Genel Namespace diğer adlarını kullanma](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span><span class="sxs-lookup"><span data-stu-id="0ea7e-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ea7e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ea7e-105">Example</span></span>

<span data-ttu-id="0ea7e-106">Aşağıdaki örnek nasıl kullanılacağını gösterir `global` belirtmek için bağlamsal anahtar sözcük sınıfı `TestApp` genel ad alanında tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="0ea7e-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="0ea7e-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ea7e-107">See also</span></span>

- [<span data-ttu-id="0ea7e-108">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="0ea7e-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)