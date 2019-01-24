---
title: Friend derlemesi başvurusu &lt;başvuru&gt; geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: cdedcc18aa82f6efd8c52cdca5d915d7d78e269f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611936"
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Friend derlemesi başvurusu &lt;başvuru&gt; geçersiz
Friend derlemesi başvurusu \<başvuru > geçersiz. Kesin ad imzalı derlemelerin kendi InternalsVisibleTo bildirmelerinde bir ortak anahtar belirtmeniz gerekir.  
  
 Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucusunda bir katı adlı derlemeyi tanımlar, ancak bunu içermemesi bir `PublicKey` özniteliği.  
  
 **Hata Kimliği:** BC31535  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ortak anahtar tanımlayıcı adlı arkadaş derleme için belirleyin. Geçirilen derleme adının bir parçası olarak ortak anahtarı içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik Oluşturucusu kullanarak `PublicKey` özniteliği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Reflection.AssemblyName>
- [Arkadaş Bütünleştirilmiş Kodları](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)


