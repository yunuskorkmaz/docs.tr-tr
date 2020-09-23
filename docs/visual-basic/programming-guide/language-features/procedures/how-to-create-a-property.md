---
title: 'Nasıl yapılır: Özellik Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: bd138177d5f4b7ee1eb63833360d227baa54f66d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072749"
---
# <a name="how-to-create-a-property-visual-basic"></a>Nasıl yapılır: Özellik Oluşturma (Visual Basic)

Bir ifade ve bir ifade arasında bir özellik tanımı çevrelemektir `Property` `End Property` . Bu tanım içinde bir `Get` yordam, `Set` yordam veya her ikisini de tanımlarsınız. Tüm özellik kodu bu yordamların içinde yer alır.  
  
 `Get`Yordam, özelliğin değerini alır ve `Set` yordam bir değer depolar. Özelliğin okuma/yazma erişimine sahip olmasını istiyorsanız her iki yordamı da tanımlamanız gerekir. Salt okunurdur bir özellik için, yalnızca tanımlarsınız ve yalnızca `Get` bir salt yazılır özellik için tanımlarsınız `Set` .  
  
### <a name="to-create-a-property"></a>Bir özellik oluşturmak için  
  
1. Herhangi bir özellik veya yordamın dışında, bir [Property ifadesini](../../../language-reference/statements/property-statement.md)ve ardından bir `End Property` ifadesini kullanın.  
  
2. Özelliği parametreleri alırsa, `Property` yordam adı ile anahtar sözcüğü, sonra parantez içindeki parametre listesini izleyin.  
  
3. `As`Özelliğin değerinin veri türünü belirtmek için bir yan tümcesiyle ayraçları izleyin. Salt yazılır bir özellik için bile veri türünü belirtmeniz gerekir.  
  
4. `Get`Ve `Set` yordamlarını uygun şekilde ekleyin. Aşağıdaki yönergelere bakın.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Bir özellik değeri alan bir Get yordamı oluşturmak için  
  
1. `Property`Ve deyimleri arasında bir `End Property` [Get deyimi](../../../language-reference/statements/get-statement.md), ardından bir `End Get` deyimi yazın. Yordam için herhangi bir parametre tanımlamanız gerekmez `Get` .  
  
2. Ve deyimleri arasında özelliğin değerini almak için kod deyimlerini yerleştirin `Get` `End Get` . Bu kod, özelliğin değerini oluşturma ve döndürmenin yanı sıra diğer hesaplamalar ve veri düzenlemeleri içerebilir.  
  
3. `Return`Özelliğin değerini çağıran koda döndürmek için bir ifade kullanın.  
  
 `Get`Okuma-yazma özelliği için ve salt okunurdur özelliği için bir yordam yazmanız gerekir. `Get`Salt yazılır özellik için bir yordam tanımlamamalısınız.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Özelliğin değerini yazan bir ayarlama yordamı oluşturmak için  
  
1. `Property`Ve deyimleri arasında bir `End Property` [set deyimi](../../../language-reference/statements/set-statement.md)ve ardından bir `End Set` deyimi yazın.  
  
2. `Set`İfadesinde, `Set` parantez içinde bir parametre listesi ile anahtar sözcüğünü izleyin. Bu parametre listesi, çağıran kodun geçirilmiş değeri için en az bir değer parametresi içermelidir. Bu değer parametresinin varsayılan adı vardır `Value` ancak uygunsa farklı bir ad kullanabilirsiniz. Değer parametresi, özelliğin kendisiyle aynı veri türüne sahip olmalıdır.  
  
3. Ve deyimleri arasındaki özellikte bir değeri depolamak için kod deyimlerini yerleştirin `Set` `End Set` . Bu kod, özelliğin değerini doğrulamaya ve depolamaya ek olarak diğer hesaplamalar ve veri düzenlemeleri içerebilir.  
  
4. Çağıran kodun sağladığı değeri kabul etmek için value parametresini kullanın. Bu değeri doğrudan bir atama deyiminde saklayabilir veya depolanacağı iç değeri hesaplamak için bir ifadede kullanabilirsiniz.  
  
 `Set`Okuma-yazma özelliği için ve salt yazılır bir özellik için bir yordam yazmanız gerekir. `Set`Salt okunurdur özelliği için bir yordam tanımlamamalısınız.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, tam adı iki anayent adı, ilk adı ve soyadı olarak depolayan bir okuma/yazma özelliği oluşturur. Çağıran kod okuduğunda `fullName` , `Get` yordam iki anayent adı birleştirir ve tam adı döndürür. Çağıran kod yeni bir tam ad atarken, `Set` yordam onu iki anayada bölmek için çalışır. Bir boşluk bulamazsa, ilk ad olarak tümünü depolar.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 Aşağıdaki örnek, öğesinin özellik yordamlarına yapılan tipik çağrıları gösterir `fullName` . İlk çağrı, özellik değerini ayarlar ve ikinci çağrı onu alır.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](./index.md)
- [Özellik Yordamları](./property-procedures.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Visual Basic'de Özellikler ve Değişkenler Arasındaki Farklar](./differences-between-properties-and-variables.md)
- [Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Nasıl yapılır: Bir Özellik Yordamı Çağırma](./how-to-call-a-property-procedure.md)
- [Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma](./how-to-declare-and-call-a-default-property.md)
- [Nasıl yapılır: Bir Özelliğe Değer Ekleme](./how-to-put-a-value-in-a-property.md)
- [Nasıl yapılır: Bir Özellikten Değer Alma](./how-to-get-a-value-from-a-property.md)
