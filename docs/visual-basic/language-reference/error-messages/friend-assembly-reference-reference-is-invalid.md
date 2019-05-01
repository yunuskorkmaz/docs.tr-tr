---
title: <reference> arkadaş derleme başvurusu geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 0c1526e32ddc64cb4124c6f8205d58deef911dd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802486"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="f5836-102">Friend derlemesi başvurusu \<başvuru > geçersiz</span><span class="sxs-lookup"><span data-stu-id="f5836-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="f5836-103">Friend derlemesi başvurusu \<başvuru > geçersiz.</span><span class="sxs-lookup"><span data-stu-id="f5836-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="f5836-104">Kesin ad imzalı derlemelerin kendi InternalsVisibleTo bildirmelerinde bir ortak anahtar belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f5836-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="f5836-105">Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucusunda bir katı adlı derlemeyi tanımlar, ancak bunu içermemesi bir `PublicKey` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f5836-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="f5836-106">**Hata Kimliği:** BC31535</span><span class="sxs-lookup"><span data-stu-id="f5836-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5836-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f5836-107">To correct this error</span></span>  
  
1. <span data-ttu-id="f5836-108">Ortak anahtar tanımlayıcı adlı arkadaş derleme için belirleyin.</span><span class="sxs-lookup"><span data-stu-id="f5836-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="f5836-109">Geçirilen derleme adının bir parçası olarak ortak anahtarı içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik Oluşturucusu kullanarak `PublicKey` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f5836-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5836-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5836-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="f5836-111">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="f5836-111">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
