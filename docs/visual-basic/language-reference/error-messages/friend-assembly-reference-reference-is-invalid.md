---
title: <reference> arkadaş derleme başvurusu geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 0966cea26c5dde8f116081c7a6411b4275e50f40
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817051"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="da4b4-102">Friend derlemesi başvurusu \<başvuru > geçersiz</span><span class="sxs-lookup"><span data-stu-id="da4b4-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="da4b4-103">Friend derlemesi başvurusu \<başvuru > geçersiz.</span><span class="sxs-lookup"><span data-stu-id="da4b4-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="da4b4-104">Kesin ad imzalı derlemelerin kendi InternalsVisibleTo bildirmelerinde bir ortak anahtar belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="da4b4-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="da4b4-105">Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucusunda bir katı adlı derlemeyi tanımlar, ancak bunu içermemesi bir `PublicKey` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="da4b4-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="da4b4-106">**Hata Kimliği:** BC31535</span><span class="sxs-lookup"><span data-stu-id="da4b4-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da4b4-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="da4b4-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="da4b4-108">Ortak anahtar tanımlayıcı adlı arkadaş derleme için belirleyin.</span><span class="sxs-lookup"><span data-stu-id="da4b4-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="da4b4-109">Geçirilen derleme adının bir parçası olarak ortak anahtarı içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik Oluşturucusu kullanarak `PublicKey` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="da4b4-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4b4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da4b4-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="da4b4-111">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="da4b4-111">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
