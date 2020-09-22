---
title: <reference> arkadaş derleme başvurusu geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: 72c030d18d5339908c5088e104f6a8ad3e76943b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874092"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>\<reference> arkadaş derleme başvurusu geçersiz

Arkadaş derleme başvurusu \<reference> geçersiz. Tanımlayıcı adı imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmesi gerekir.  
  
 Öznitelik oluşturucusuna geçirilen derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> , tanımlayıcı adlı bir derlemeyi tanımlar, ancak bir `PublicKey` özniteliği içermez.  
  
 **Hata kimliği:** BC31535  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Tanımlayıcı adlı Friend derlemesi için ortak anahtarı belirleme. Özniteliği kullanılarak öznitelik oluşturucusuna geçirilen derleme adının bir parçası olarak ortak anahtarı ekleyin <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `PublicKey` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- [Arkadaş derlemeleri](../../../standard/assembly/friend.md)
