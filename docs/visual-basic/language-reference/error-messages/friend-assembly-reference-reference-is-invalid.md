---
title: <reference> arkadaş derleme başvurusu geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: ff2cdbebe13f6224209ef8da62600c99348c911b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286825"
---
# <a name="friend-assembly-reference-reference-is-invalid"></a>Friend derlemesi başvurusu \<başvuru > geçersiz
Friend derlemesi başvurusu \<başvuru > geçersiz. Kesin ad imzalı derlemelerin kendi InternalsVisibleTo bildirmelerinde bir ortak anahtar belirtmeniz gerekir.  
  
 Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucusunda bir katı adlı derlemeyi tanımlar, ancak bunu içermemesi bir `PublicKey` özniteliği.  
  
 **Hata Kimliği:** BC31535  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ortak anahtar tanımlayıcı adlı arkadaş derleme için belirleyin. Geçirilen derleme adının bir parçası olarak ortak anahtarı içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik Oluşturucusu kullanarak `PublicKey` özniteliği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Reflection.AssemblyName>
- [Arkadaş Bütünleştirilmiş Kodları](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)


