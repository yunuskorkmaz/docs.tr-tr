---
title: Temel sınıfı 'System.MarshalByRefObject' olan '<name>' sınıfında bulunan değer türündeki '<name>' alanının bir üyesi olduğundan, '<classname>' öğesine başvurulamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
ms.openlocfilehash: c29d3def2299dc1d7e3b084b3408b3f919addc63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279597"
---
# <a name="cannot-refer-to-name-because-it-is-a-member-of-the-value-typed-field-name-of-class-classname-which-has-systemmarshalbyrefobject-as-a-base-class"></a>Başvurulamaz '\<adı >' değer alanının bir üyesi olduğundan '\<adı >' sınıfının\<SınıfAdı >' temel sınıfı ' System.MarshalByRefObject' olan
`System.MarshalByRefObject` Sınıfı uygulama etki alanı sınırları uzak nesnelere erişimi destekleyen uygulamalar sağlar. Türleri devralmalıdır `MarshalByRejectObject` sınıf türü uygulama etki alanı sınırlarında kullanıldığında. Bir nesnenin üyelerine oluşturulmuş olan uygulama etki alanı dışında kullanılabilir olmadığı için nesne durumunu kopyalanmayacak.  
  
 **Hata Kimliği:** BC30310  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurulan üyenin geçerli olduğundan emin olmak için başvuru denetleyin.  
  
2.  Açıkça üyesiyle uygun `Me` anahtar sözcüğü.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.MarshalByRefObject>
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
