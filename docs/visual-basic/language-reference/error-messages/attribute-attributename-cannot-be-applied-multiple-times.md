---
description: "Şu konuda daha fazla bilgi edinin: BC30663: ' <attributename> ' özniteliği birden çok kez uygulanamaz"
title: "'<attributename>' özniteliği bir defadan fazla uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 84b77111a7401eb6f30eb7cd167f4b5689f33e77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797152"
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
