---
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 27cbe6d0043179c4a5d52baae06bad805f9d1d3a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162667"
---
# <a name="bc30663-attribute-attributename-cannot-be-applied-multiple-times"></a>BC30663: ' \<attributename> ' özniteliği birden çok kez uygulanamaz

Özniteliği yalnızca bir kez uygulanabilir. `AttributeUsage`Özniteliği bir özniteliğin birden çok kez uygulanıp uygulanamayacağını belirler.

 **Hata kimliği:** BC30663

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Özniteliğin yalnızca bir kez uygulandığından emin olun.

2. Geliştirdiğiniz özel öznitelikleri kullanıyorsanız, `AttributeUsage` Aşağıdaki örnekte olduğu gibi, özniteliğini birden çok öznitelik kullanımına izin verecek şekilde değiştirmeyi düşünün.

```vb
<AttributeUsage(AllowMultiple := True)>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AttributeUsageAttribute>
- [Özel Öznitelikler Oluşturma](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../programming-guide/concepts/attributes/attributeusage.md)
