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
ms.openlocfilehash: ab1c7c5cc7a7f4ad899df7722769238e05d96e6b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
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
 

