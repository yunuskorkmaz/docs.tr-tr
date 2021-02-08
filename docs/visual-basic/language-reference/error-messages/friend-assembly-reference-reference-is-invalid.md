---
description: 'Hakkında daha fazla bilgi edinin: BC31535: arkadaş derleme başvurusu <reference> geçersiz'
title: <reference> arkadaş derleme başvurusu geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: e3e08edede9bee4710c415a61592857229ea4f35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796203"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a>BC31535: arkadaş derleme başvurusu \<reference> geçersiz

Arkadaş derleme başvurusu \<reference> geçersiz. Tanımlayıcı adı imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmesi gerekir.

 Öznitelik oluşturucusuna geçirilen derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> , tanımlayıcı adlı bir derlemeyi tanımlar, ancak bir `PublicKey` özniteliği içermez.

 **Hata kimliği:** BC31535

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Tanımlayıcı adlı Friend derlemesi için ortak anahtarı belirleme. Özniteliği kullanılarak öznitelik oluşturucusuna geçirilen derleme adının bir parçası olarak ortak anahtarı ekleyin <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `PublicKey` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- [Arkadaş derlemeleri](../../../standard/assembly/friend.md)
