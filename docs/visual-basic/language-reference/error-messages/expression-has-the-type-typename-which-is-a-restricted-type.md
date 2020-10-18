---
title: İfade kısıtlanmış bir tür olan '<typename>' türüne sahip ve 'Object' veya 'ValueType' öğesinden devralınan üyelere erişim için kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 3e19c0d71ee47ac61e9704f0fcd2637f01aa0896
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163057"
---
# <a name="bc31393-expression-has-the-type-typename-which-is-a-restricted-type-and-cannot-be-used-to-access-members-inherited-from-object-or-valuetype"></a>BC31393: Ifadesi \<typename> kısıtlanmış bir tür olan ' ' türüne sahip ve ' Object ' veya ' ValueType ' öğesinden devralınan üyelere erişim için kullanılamaz

Bir ifade, ortak dil çalışma zamanı (CLR) tarafından kutulanmamış ancak paketleme gerektiren bir üyeye erişebilen bir tür olarak değerlendirilir.

 *Kutulama* , bir türü veya ne kadar bir türe dönüştürmek için gereken işleme anlamına gelir `Object` <xref:System.ValueType> . Ortak dil çalışma zamanı belirli yapı türlerini (örneğin, ve) <xref:System.ArgIterator> , <xref:System.RuntimeArgumentHandle> <xref:System.TypedReference>

 Bu ifade, veya gibi devralınan bir yöntemi çağırmak için kısıtlanmış türü kullanmaya çalışır <xref:System.Object> <xref:System.ValueType> <xref:System.Object.GetHashCode%2A> <xref:System.Object.ToString%2A> . Bu yönteme erişmek için Visual Basic, bu hataya neden olan bir örtük paketleme dönüştürmesi denemiştir.

 **Hata kimliği:** BC31393

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Alıntı yapılan tür sonucunu veren ifadeyi bulun.

2. Veya ' den devralınan yöntemi çağırmayı deneyen deyiminiz kısmını bulun <xref:System.Object> <xref:System.ValueType> .

3. Yöntem çağrısından kaçınmak için ifadeyi yeniden yazın.

## <a name="see-also"></a>Ayrıca bkz.

- [Örtük ve Açık Dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
