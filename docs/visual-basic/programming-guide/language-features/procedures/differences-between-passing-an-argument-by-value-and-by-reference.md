---
title: Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: f9fdb1e98fb827391b615f5fe0afd1ee43c9f8e1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075050"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Değere ve Başvuruya Göre Bağımsız Değişken Geçirme Arasındaki Farklar (Visual Basic)

Bir yordama bir veya daha fazla bağımsız değişken geçirdiğinizde, her bağımsız değişken çağıran koddaki temel bir programlama öğesine karşılık gelir. Bu temel öğenin veya buna bir başvurunun değerini geçirebilirsiniz. Bu, *geçirme mekanizması*olarak bilinir.  
  
## <a name="passing-by-value"></a>Değere göre geçirme  

 Yordam tanımındaki karşılık gelen parametrenin [ByVal](../../../language-reference/modifiers/byval.md) anahtar sözcüğünü belirterek *değere göre* bir bağımsız değişken geçirirsiniz. Bu geçen mekanizmayı kullandığınızda Visual Basic, temeldeki programlama öğesinin değerini yordamdaki bir yerel değişkene kopyalar. Yordam kodu, çağıran koddaki temel alınan öğeye hiçbir erişime sahip değil.  
  
## <a name="passing-by-reference"></a>Başvuruya göre geçirme  

 Yordam tanımında karşılık gelen parametre için [ByRef](../../../language-reference/modifiers/byref.md) anahtar sözcüğünü belirterek bir bağımsız değişkeni *başvuruya göre* geçirirsiniz. Bu geçiş mekanizmasını kullandığınızda Visual Basic, yordama çağıran koddaki temeldeki programlama öğesine doğrudan başvuru verir.  
  
## <a name="passing-mechanism-and-element-type"></a>Geçirme mekanizması ve öğe türü  

 Geçirme mekanizması seçimi, temel öğe türünün sınıflandırmasıyla aynı değildir. Değere veya başvuruya göre geçirme, yordam koduna ne Visual Basic temin eder. Bir değer türü veya başvuru türü, bir programlama öğesinin bellekte nasıl depolandığını belirtir.  
  
 Ancak, geçen mekanizma ve öğe türü birbirleriyle ilişkilidir. Başvuru türünün değeri, belleğin başka bir yerindeki verilerin bir işaretçisidir. Yani, bir başvuru türü değere göre geçirdiğinizde, yordam kodunun temeldeki öğenin kendisine erişemese de, temel alınan öğenin verilerine yönelik bir işaretçisi vardır. Örneğin, öğe bir dizi değişkenidir, yordam kodu değişkene erişemez, ancak dizi üyelerine erişebilir.  
  
## <a name="ability-to-modify"></a>Değiştirme özelliği  

 Değiştirilemeyen bir öğeyi bağımsız değişken olarak geçirdiğinizde, yordam, veya geçirilmemişse, çağıran kodda herhangi bir zaman değişiklik yapabilir `ByVal` `ByRef` .  
  
 Değiştirilebilir bir öğe için aşağıdaki tablo, öğe türü ve geçen mekanizma arasındaki etkileşimi özetler.  
  
|Öğe türü|Geçiril `ByVal`|Geçiril `ByRef`|  
|------------------|--------------------|--------------------|  
|Değer türü (yalnızca bir değer içerir)|Yordam, ya da üyelerini değiştiremez.|Yordam değişkeni ve üyelerini değiştirebilir.|  
|Başvuru türü (bir sınıf veya yapı örneğine yönelik bir işaretçi içerir)|Yordam değişkeni değiştiremez, ancak gösterdiği örnek üyelerini değiştirebilir.|Yordam, işaret ettiği örnek değişkenini ve üyelerini değiştirebilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Nasıl yapılır: Bir Yordama Bağımsız Değişkenler Geçirme](./how-to-pass-arguments-to-a-procedure.md)
- [Bağımsız Değişkenleri Değere ve Başvuruya Göre Geçirme](./passing-arguments-by-value-and-by-reference.md)
- [Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkeninin Değerini Değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)
- [Nasıl yapılır: Bir Yordam Bağımsız Değişkenini Değer Değişikliklerine Karşı Koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Nasıl yapılır: Bağımsız Değişkeni Değere Göre Geçirilecek Şekilde Zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Bağımsız Değişkenleri Konuma ve Ada Göre Geçirme](./passing-arguments-by-position-and-by-name.md)
- [Değer Türleri ve Başvuru Türleri](../data-types/value-types-and-reference-types.md)
