---
title: Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: de4800e23519c2cc1c8b2b219287b9fa018b9bbf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864580"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar
Değişkenleri ve özellikleri erişebileceğiniz değerleri temsil eder. Ancak, depolama ve uygulama farklılıklar vardır.  
  
## <a name="variables"></a>Değişkenler  
 A *değişkeni* doğrudan bir bellek konumuna karşılık gelir. Bir tek bir bildirim deyiminin sahip bir değişken tanımlayın. Bir değişken olabilir bir *yerel değişken*bir yordam içinde ve yalnızca bu yordam içinde tanımlanan veya olabilir bir *üye değişkeni*, içindeki herhangi bir modül, sınıf veya yapı içinde tanımlanan yordam. Üye değişkeni olarak da adlandırılır bir *alan*.  
  
## <a name="properties"></a>Özellikler  
 A *özelliği* bir modül, sınıf ya da yapı üzerinde tanımlı bir veri öğesi. Bir kod bloğu arasında olan bir özelliği tanımla `Property` ve `End Property` deyimleri. Kod bloğunu içeren bir `Get` yordamı, bir `Set` yordamı veya her ikisi. Bu yordamlar adlı *özellik yordamları* veya *özellik erişimcileri*. Alma veya özellik değerini depolamak ek olarak, erişim sayacı güncelleştirme gibi eylemler özel,'ne de gerçekleştirebilirsiniz.  
  
## <a name="differences"></a>Farkları  
 Aşağıdaki tabloda, değişkenleri ve özellikleri arasında bazı önemli farklar gösterilmektedir.  
  
|Fark noktası|Değişken|Özellik|  
|-------------------------|--------------|--------------|  
|Bildirim|Tek bildirimde deyimi|Bir kod bloğu içindeki deyimler serisini|  
|Uygulama|Tek bir depolama konumu|Yürütülebilir kod (özellik yordamları)|  
|Depolama|Doğrudan değişkenin değeriyle ilişkili|Genellikle iç depolama alanına özelliğin içeren sınıfı veya modülü dışında kullanılamaz sahip<br /><br /> Özelliğin değerini olabilir veya depolanmış bir öğe olarak mevcut olmayabilir <sup>1</sup>|  
|Yürütülebilir kod|Yok.|En az bir yordam olmalıdır|  
|Okuma ve yazma erişimi|Okuma/yazma veya salt okunur|Okuma/yazma, salt okunur veya salt yazılır|  
|(Ek olarak kabul etme veya değer döndürme) özel eylemler|Olası değil|Özellik değerini alma veya ayarlama kapsamında gerçekleştirilebilir|  
  
 <sup>1</sup> depolama doğrudan tek bir öğe için bir değişken, bir özelliğin değerini karşılık gelmeyebilir. Depolama, kolaylık veya güvenlik için parçalara bölmek veya değeri bir şifrelenmiş biçimde depolanabilir. Bu gibi durumlarda `Get` yordamı veya parçaları bir araya getirin, depolanmış değerin şifresi ve `Set` yordamı yeni değer şifrelenemedi mi bağlı depolama alanına bölün. Bir özellik değeri, bu durumda, günün bir saati gibi geçici olabilir `Get` yordamı hesaplamak, çalışma sırasında özellik erişim her zaman.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Nasıl yapılır: Özellik oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
