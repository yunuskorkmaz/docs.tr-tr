---
title: Genel bağlamsal anahtar sözcük C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 9a8c7b5134cc29668aae53e8a3f86ddae4c8263a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627690"
---
# <a name="global-c-reference"></a><span data-ttu-id="c13e3-102">global (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c13e3-102">global (C# Reference)</span></span>

<span data-ttu-id="c13e3-103">Bağlam anahtar sözcüğü, [:: işlecinden](../operators/namespace-alias-qualifier.md)önce geldiğinde, herhangi bir C# program için varsayılan ad alanı olan genel ad alanına başvurur ve aksi durumda adlandırılmamış olur. `global`</span><span class="sxs-lookup"><span data-stu-id="c13e3-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifier.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="c13e3-104">Daha fazla bilgi için [nasıl yapılır: Genel ad alanı diğer adını](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="c13e3-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="c13e3-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c13e3-105">Example</span></span>

<span data-ttu-id="c13e3-106">Aşağıdaki örnek, sınıfının `global` `TestApp` genel ad alanında tanımlandığını belirtmek için bağlamsal anahtar sözcüğünün nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c13e3-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="c13e3-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c13e3-107">See also</span></span>

- [<span data-ttu-id="c13e3-108">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="c13e3-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
