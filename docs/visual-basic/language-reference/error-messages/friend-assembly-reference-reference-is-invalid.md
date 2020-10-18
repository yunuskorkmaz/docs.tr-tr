---
title: <reference> arkadaş derleme başvurusu geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: a42dd99ffaa06dce4823ce5d022fac02ae99c6bd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160717"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="229df-102">BC31535: arkadaş derleme başvurusu \<reference> geçersiz</span><span class="sxs-lookup"><span data-stu-id="229df-102">BC31535: Friend assembly reference \<reference> is invalid</span></span>

<span data-ttu-id="229df-103">Arkadaş derleme başvurusu \<reference> geçersiz.</span><span class="sxs-lookup"><span data-stu-id="229df-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="229df-104">Tanımlayıcı adı imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="229df-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>

 <span data-ttu-id="229df-105">Öznitelik oluşturucusuna geçirilen derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> , tanımlayıcı adlı bir derlemeyi tanımlar, ancak bir `PublicKey` özniteliği içermez.</span><span class="sxs-lookup"><span data-stu-id="229df-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>

 <span data-ttu-id="229df-106">**Hata kimliği:** BC31535</span><span class="sxs-lookup"><span data-stu-id="229df-106">**Error ID:** BC31535</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="229df-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="229df-107">To correct this error</span></span>

1. <span data-ttu-id="229df-108">Tanımlayıcı adlı Friend derlemesi için ortak anahtarı belirleme.</span><span class="sxs-lookup"><span data-stu-id="229df-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="229df-109">Özniteliği kullanılarak öznitelik oluşturucusuna geçirilen derleme adının bir parçası olarak ortak anahtarı ekleyin <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `PublicKey` .</span><span class="sxs-lookup"><span data-stu-id="229df-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="229df-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="229df-110">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="229df-111">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="229df-111">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
