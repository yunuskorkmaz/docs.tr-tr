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
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Arkadaş derleme başvurusu &lt;başvuru&gt; geçersiz
Arkadaş derleme başvurusu \<başvuru > geçersiz. Tanımlayıcı ad imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmeniz gerekir.  
  
 Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucunun tanımlayıcı adlı bir derleme tanımlar, ancak yer almaz bir `PublicKey` özniteliği.  
  
 **Hata Kimliği:** BC31535  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tanımlayıcı adlı arkadaş derleme için ortak anahtar belirleyin. Derleme adı parçası geçirilen gibi ortak anahtar içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> kullanarak öznitelik oluşturucunun `PublicKey` özniteliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.AssemblyName>  
 [Arkadaş Bütünleştirilmiş Kodları](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

