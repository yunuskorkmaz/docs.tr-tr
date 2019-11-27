---
title: Özellikler ile Değişkenler Arasındaki Farklar
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
ms.openlocfilehash: bbed3248840803d36607a67c8373fed15c07445f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341216"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar
Değişkenler ve özellikler, erişebileceğiniz değerleri temsil eder. Ancak, depolama ve uygulamada farklılıklar vardır.  
  
## <a name="variables"></a>Değişkenler  
 *Değişken* doğrudan bir bellek konumuna karşılık gelir. Tek bir bildirim bildirimiyle bir değişken tanımlarsınız. Bir değişken, bir yordamda tanımlanmış ve yalnızca bu yordamda kullanılabilen bir *yerel değişken*olabilir ya da bir modül, sınıf veya yapıda tanımlanmış, ancak herhangi bir yordamda tanımlanmış bir *üye değişkeni*olabilir. Bir üye değişkeni de *alan*olarak adlandırılır.  
  
## <a name="properties"></a>Özellikler  
 Bir *özellik* , modül, sınıf veya yapıda tanımlanmış bir veri öğesidir. `Property` ve `End Property` deyimleri arasında kod bloğu içeren bir özellik tanımlarsınız. Kod bloğu `Get` yordam, `Set` yordamı veya her ikisini de içerir. Bu yordamlar, *özellik yordamları* veya *özellik erişimcileri*olarak adlandırılır. Özelliğin değerini almaya veya depolamaya ek olarak, bir erişim sayacını güncelleştirme gibi özel eylemler de gerçekleştirebilirler.  
  
## <a name="differences"></a>Fark  
 Aşağıdaki tabloda, değişkenler ve özellikler arasındaki bazı önemli farklılıklar gösterilmektedir.  
  
|Fark noktası|Değişken|Özellik|  
|-------------------------|--------------|--------------|  
|Bildirim|Single bildirim ekstresi|Kod bloğundaki deyim dizisi|  
|Uygulama|Tek depolama konumu|Yürütülebilir kod (özellik yordamları)|  
|Depolama|Değişken değeriyle doğrudan ilişkili|Genellikle, özelliğin kapsayan sınıf veya modül dışında kullanılamayan iç depolama alanı vardır<br /><br /> Özelliğin değeri, depolanan bir öğe olarak olabilir veya mevcut olmayabilir <sup>1</sup>|  
|Yürütülebilir kod|Yok.|En az bir yordam olmalıdır|  
|Okuma ve yazma erişimi|Okuma/yazma veya salt okuma|Okuma/yazma, salt okunurdur veya salt yazılır|  
|Özel eylemler (değerin kabul edilmesi veya döndürülmesinin yanı sıra)|Mümkün değil|Özellik değerinin ayarlanması veya alınması kapsamında gerçekleştirilebilir|  
  
 <sup>1</sup> bir değişkenin aksine, bir özelliğin değeri doğrudan tek bir depolama öğesine karşılık gelmeyebilir. Depolama, kolaylık veya güvenlik için parçalara ayrılabilir veya değer şifrelenmiş bir biçimde depolanabilir. Bu durumlarda `Get` yordamı, parçaları birleştirir veya depolanan değerin şifresini çözer ve `Set` yordamı yeni değeri şifreleyerek veya onu yapısal depolamaya bölecektir. Özellik değeri, günün saati gibi kısa ömürlü olabilir ve bu durumda `Get` yordam, özelliğe her eriştiğinizde bu işlemi bir kez hesaplayabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Property Deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Nasıl yapılır: Özellik Oluşturma](./how-to-create-a-property.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
