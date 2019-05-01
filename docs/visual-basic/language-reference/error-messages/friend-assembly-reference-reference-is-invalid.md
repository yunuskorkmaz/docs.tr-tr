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
# <a name="friend-assembly-reference-reference-is-invalid"></a>Friend derlemesi başvurusu \<başvuru > geçersiz
Friend derlemesi başvurusu \<başvuru > geçersiz. Kesin ad imzalı derlemelerin kendi InternalsVisibleTo bildirmelerinde bir ortak anahtar belirtmeniz gerekir.  
  
 Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucusunda bir katı adlı derlemeyi tanımlar, ancak bunu içermemesi bir `PublicKey` özniteliği.  
  
 **Hata Kimliği:** BC31535  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Ortak anahtar tanımlayıcı adlı arkadaş derleme için belirleyin. Geçirilen derleme adının bir parçası olarak ortak anahtarı içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik Oluşturucusu kullanarak `PublicKey` özniteliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.AssemblyName>
- [Arkadaş Bütünleştirilmiş Kodları](../../../standard/assembly/friend-assemblies.md)
