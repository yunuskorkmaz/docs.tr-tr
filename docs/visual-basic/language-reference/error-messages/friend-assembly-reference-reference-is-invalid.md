---
title: "Arkadaş derleme başvurusu &lt;başvuru&gt; geçersiz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Arkadaş derleme başvurusu &lt;başvuru&gt; geçersiz
Arkadaş derleme başvurusu \<başvuru > geçersiz. Tanımlayıcı ad imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmeniz gerekir.  
  
 Derleme adı geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik oluşturucunun tanımlayıcı adlı bir derleme tanımlar, ancak yer almaz bir `PublicKey` özniteliği.  
  
 **Hata Kimliği:** BC31535  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tanımlayıcı adlı arkadaş derleme için ortak anahtar belirleyin. Derleme adı parçası geçirilen gibi ortak anahtar içeren <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> kullanarak öznitelik oluşturucunun `PublicKey` özniteliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.AssemblyName>  
 [Arkadaş derlemeleri](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)
