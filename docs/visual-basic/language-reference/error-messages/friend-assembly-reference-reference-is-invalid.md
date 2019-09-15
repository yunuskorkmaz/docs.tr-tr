---
title: <reference> arkadaş derleme başvurusu geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 6eb46c6479adc69eaf65b34c69aa69977b4d62ef
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972388"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="ee2ab-102">Friend bütünleştirilmiş kod \<başvurusu başvuru > geçersiz</span><span class="sxs-lookup"><span data-stu-id="ee2ab-102">Friend assembly reference \<reference> is invalid</span></span>
<span data-ttu-id="ee2ab-103">Friend bütünleştirilmiş kod \<başvurusu başvuru > geçersiz.</span><span class="sxs-lookup"><span data-stu-id="ee2ab-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="ee2ab-104">Tanımlayıcı adı imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee2ab-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="ee2ab-105"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Öznitelik oluşturucusuna geçirilen derleme adı, tanımlayıcı adlı bir derlemeyi tanımlar, ancak bir `PublicKey` özniteliği içermez.</span><span class="sxs-lookup"><span data-stu-id="ee2ab-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="ee2ab-106">**Hata KIMLIĞI:** BC31535</span><span class="sxs-lookup"><span data-stu-id="ee2ab-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ee2ab-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ee2ab-107">To correct this error</span></span>  
  
1. <span data-ttu-id="ee2ab-108">Tanımlayıcı adlı Friend derlemesi için ortak anahtarı belirleme.</span><span class="sxs-lookup"><span data-stu-id="ee2ab-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="ee2ab-109"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Özniteliği`PublicKey` kullanılarak öznitelik oluşturucusuna geçirilen derleme adının bir parçası olarak ortak anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ee2ab-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2ab-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee2ab-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="ee2ab-111">Arkadaş Bütünleştirilmiş Kodları</span><span class="sxs-lookup"><span data-stu-id="ee2ab-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
