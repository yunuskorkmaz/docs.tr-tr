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
# <a name="friend-assembly-reference-reference-is-invalid"></a>Friend bütünleştirilmiş kod \<başvurusu başvuru > geçersiz
Friend bütünleştirilmiş kod \<başvurusu başvuru > geçersiz. Tanımlayıcı adı imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmesi gerekir.  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Öznitelik oluşturucusuna geçirilen derleme adı, tanımlayıcı adlı bir derlemeyi tanımlar, ancak bir `PublicKey` özniteliği içermez.  
  
 **Hata KIMLIĞI:** BC31535  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Tanımlayıcı adlı Friend derlemesi için ortak anahtarı belirleme. <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Özniteliği`PublicKey` kullanılarak öznitelik oluşturucusuna geçirilen derleme adının bir parçası olarak ortak anahtarı ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- [Arkadaş Bütünleştirilmiş Kodları](../../../standard/assembly/friend.md)
