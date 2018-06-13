---
title: Arkadaş derleme başvurusu &lt;başvuru&gt; geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: c47fae9c60dc04ee02b1ff015d3dde87b8920c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587377"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="0489a-102">Arkadaş derleme başvurusu &lt;başvuru&gt; geçersiz</span><span class="sxs-lookup"><span data-stu-id="0489a-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="0489a-103">Arkadaş derleme başvurusu \<başvuru > geçersiz.</span><span class="sxs-lookup"><span data-stu-id="0489a-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="0489a-104">Tanımlayıcı ad imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0489a-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="0489a-105">Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucunun tanımlayıcı adlı bir derleme tanımlar, ancak yer almaz bir `PublicKey` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0489a-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="0489a-106">**Hata Kimliği:** BC31535</span><span class="sxs-lookup"><span data-stu-id="0489a-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0489a-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0489a-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="0489a-108">Tanımlayıcı adlı arkadaş derleme için ortak anahtar belirleyin.</span><span class="sxs-lookup"><span data-stu-id="0489a-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="0489a-109">Derleme adı parçası geçirilen gibi ortak anahtar içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> kullanarak öznitelik oluşturucunun `PublicKey` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0489a-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0489a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0489a-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="0489a-111">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="0489a-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

