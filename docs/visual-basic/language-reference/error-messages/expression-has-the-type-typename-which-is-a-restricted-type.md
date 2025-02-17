---
description: "Hakkında daha fazla bilgi edinin: BC31393: Ifadesi <typename> kısıtlanmış bir tür olan ' ' türüne sahip ve ' Object ' veya ' ValueType ' öğesinden devralınan üyelere erişim için kullanılamaz"
title: İfade kısıtlanmış bir tür olan '<typename>' türüne sahip ve 'Object' veya 'ValueType' öğesinden devralınan üyelere erişim için kullanılamaz
ms.date: 07/20/2015
f1_keywords:
- bc31393
- vbc31393
helpviewer_keywords:
- BC31393
ms.assetid: 2963cf3f-c527-4aa7-b67c-ee80b6d23186
ms.openlocfilehash: 3b5f9bbb85d1645936286ea0e907e3e25764f69a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796385"
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
