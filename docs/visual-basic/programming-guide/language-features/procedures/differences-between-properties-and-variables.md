---
title: "Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cb30972e2b49a7005749f57c0223b9fa493cde52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar
Değişkenlerin ve özelliklerin erişebilmeniz için değerleri temsil eder. Ancak, depolama ve uygulama farklılıklar vardır.  
  
## <a name="variables"></a>Değişkenler  
 A *değişkeni* doğrudan bellek konumuna karşılık gelir. Bir tek bildirimi deyimi sahip bir değişken tanımlayın. Bir değişken olabilir bir *yerel değişken*yordam içindeki ve bu yordam yalnızca içinde kullanılabilir tanımlanan veya olabilir bir *üye değişkeni*, bir modül, sınıf veya yapı ancak içindeki tüm tanımlı yordam. Üye değişkeni olarak da adlandırılır bir *alan*.  
  
## <a name="properties"></a>Özellikler  
 A *özelliği* modülü, sınıf veya yapı tanımlı bir veri öğesi. Kod bloğu arasında özelliğiyle tanımladığınız `Property` ve `End Property` deyimleri. Kod bloğunu içeren bir `Get` yordamı, bir `Set` yordam veya her ikisi de. Bu yordamları adlı *özellik yordamları* veya *özellik erişimcisi*. Alma veya özelliğin değerini depolama yanı sıra, ayrıca bir erişim sayaç güncelleştirme gibi özel eylemler gerçekleştirebilirsiniz.  
  
## <a name="differences"></a>Farkları  
 Aşağıdaki tabloda, değişkenler ve özellikleri arasında önemli bazı farklar gösterilmektedir.  
  
|Fark noktası|Değişken|Özellik|  
|-------------------------|--------------|--------------|  
|Bildirim|Tek bildirimi deyimi|Kod bloğu deyimlerinde dizi|  
|Uygulama|Tek bir depolama konumu|Yürütülebilir kod (özellik yordamları)|  
|Depolama|Doğrudan değişkenin değeriyle ilişkili|Genellikle özelliğin içeren sınıf veya modülü dışında kullanılamaz iç depolama alanına sahip<br /><br /> Özelliğin değeri saklanan bir öğe var olmayabilir veya olabilir <sup>1</sup>|  
|Yürütülebilir kod|Yok.|En az bir yordam olmalıdır|  
|Okuma ve yazma erişimi|Okuma/yazma veya salt okunur|Okuma/yazma, salt okunur veya salt yazılır|  
|(Ek olarak kabul etme veya değer döndürme) özel eylemler|Mümkün değil|Ayarlama veya özellik değeri alınırken bir parçası olarak gerçekleştirilebilir|  
  
 <sup>1</sup> bir değişken depolama doğrudan tek bir öğe için bir özelliğin değerini gelmeyebilir. Depolama kolaylık veya güvenlik için parçalara bölmek veya değeri şifreli biçimde depolanabilir. Bu gibi durumlarda `Get` yordamı parçaları bir araya getirmek mi depolanan değer şifresini çözmek ve `Set` yordam yeni değer şifrelemek veya bağlı depolama alanına bölme. Bir özellik değeri, bu durumda kısa ömürlü, gün, saat gibi olabilir `Get` yordamı hesaplamak, anında özelliği her eriştiğinizde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik yordamları](./property-procedures.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Property deyimi](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Nasıl yapılır: özellik oluşturma](./how-to-create-a-property.md)  
 [Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Nasıl yapılır: bir özellik yordamı çağırma](./how-to-call-a-property-procedure.md)  
 [Nasıl yapılır: bildirme ve Visual Basic'te varsayılan özelliğini çağırın](./how-to-declare-and-call-a-default-property.md)  
 [Nasıl yapılır: bir özelliğe değer ekleme](./how-to-put-a-value-in-a-property.md)  
 [Nasıl yapılır: bir özellikten değer alma](./how-to-get-a-value-from-a-property.md)
