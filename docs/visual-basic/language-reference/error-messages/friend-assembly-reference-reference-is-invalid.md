---
title: "\n  <reference> arkadaş derleme başvurusu geçersiz"
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 796c16e912283d86496a4ccbd3b675ac1433f02d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356409"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="c9b2a-102">Friend derlemesi başvurusu \<başvuru > geçersiz</span><span class="sxs-lookup"><span data-stu-id="c9b2a-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="c9b2a-103">Friend derlemesi başvurusu \<başvuru > geçersiz.</span><span class="sxs-lookup"><span data-stu-id="c9b2a-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="c9b2a-104">Kesin ad imzalı derlemelerin kendi InternalsVisibleTo bildirmelerinde bir ortak anahtar belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9b2a-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="c9b2a-105">Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucusunda bir katı adlı derlemeyi tanımlar, ancak bunu içermemesi bir `PublicKey` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c9b2a-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="c9b2a-106">**Hata Kimliği:** BC31535</span><span class="sxs-lookup"><span data-stu-id="c9b2a-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c9b2a-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c9b2a-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="c9b2a-108">Ortak anahtar tanımlayıcı adlı arkadaş derleme için belirleyin.</span><span class="sxs-lookup"><span data-stu-id="c9b2a-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="c9b2a-109">Geçirilen derleme adının bir parçası olarak ortak anahtarı içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik Oluşturucusu kullanarak `PublicKey` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c9b2a-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b2a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9b2a-110">See also</span></span>
- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="c9b2a-111">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="c9b2a-111">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)


