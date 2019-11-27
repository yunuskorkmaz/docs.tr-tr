---
title: Yapılar ve Sınıflar
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3353935a74bb77fa4a630e706aa425063c7a610a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346325"
---
# <a name="structures-and-classes-visual-basic"></a>Yapılar ve Sınıflar (Visual Basic)
Visual Basic yapılar ve sınıfların sözdizimini birleştirir ve her iki varlığın de aynı özelliklerden çoğunu desteklediği sonuçlardır. Ancak, yapılar ve sınıflar arasında önemli farklılıklar da vardır.  
  
 Sınıfların başvuru türleri olmasının avantajı vardır; bir başvuruyu geçirmek, tüm verileriyle bir yapı değişkeni geçirilmekten daha verimlidir. Diğer yandan, yapılar genel yığında bellek ayırmayı gerektirmez.  
  
 Bir yapıdan kalıtımla almadığı için yapılar yalnızca genişletilmek zorunda olmayan nesneler için kullanılmalıdır. Oluşturmak istediğiniz nesne küçük bir örnek boyutuna sahip olduğunda yapıları kullanın ve sınıfların ve yapıların performans özelliklerini hesaba alın.  
  
## <a name="similarities"></a>Benzerlikler  
 Yapılar ve sınıflar aşağıdaki şekilde benzerdir:  
  
- Her ikisi de *kapsayıcı* türlerdir, yani diğer türleri üye olarak içerirler.  
  
- Her ikisinde de oluşturucular, Yöntemler, özellikler, alanlar, sabitler, numaralandırmalar, olaylar ve olay işleyicilerini içerebilen Üyeler vardır. Ancak, bu üyeleri bir yapının tanımlanmış *öğeleriyle* karıştırmayın.  
  
- Her ikisinin de üyeleri, kişiselleştirilmemiş erişim düzeylerine sahip olabilir. Örneğin, bir üye `Public` ve başka bir `Private`olarak bildirilebilecek.  
  
- Her ikisi de arabirim uygulayabilir.  
  
- Her ikisinde de, parametresiz veya olmayan paylaşılan oluşturucular olabilir.  
  
- Her ikisi de *varsayılan bir özellik*sunabilir, bu özellik en az bir parametre alır.  
  
- Her ikisi de olayları bildirebilir ve oluşturabilir ve her ikisi de temsilciler bildirebilir.  
  
## <a name="differences"></a>Fark  
 Yapılar ve sınıflar aşağıdaki bununla farklıdır:  
  
- Yapılar *değer türleridir*; sınıflar *başvuru türleridir*. Yapı türünün bir değişkeni, bir sınıf türü olarak veriye bir başvuru eklemek yerine yapının verilerini içerir.  
  
- Yapılar yığın ayırmayı kullanır; sınıflar yığın ayırmayı kullanır.  
  
- Tüm yapı öğeleri varsayılan olarak `Public`; sınıf değişkenleri ve sabitler varsayılan olarak `Private`, diğer sınıf üyeleri varsayılan olarak `Public`. Sınıf üyeleri için bu davranış, varsayılan Visual Basic 6,0 sistemiyle uyumluluk sağlar.  
  
- Bir yapının en az bir paylaşılmayan değişkeni veya paylaşılmayan olmayan, özel olmayan olay öğesi olması gerekir; bir sınıf tamamen boş olabilir.  
  
- Yapı öğeleri `Protected`olarak bildirilemez; sınıf üyeleri olabilir.  
  
- Bir yapı yordamı yalnızca [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) bir`Sub` yordamı ve yalnızca [AddHandler ifadesinin](../../../../visual-basic/language-reference/statements/addhandler-statement.md)yoluyla, olayları işleyebilir; herhangi bir sınıf yordamı, [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) anahtar sözcüğünü veya `AddHandler` ifadesini kullanarak olayları işleyebilir. Daha fazla bilgi için bkz. [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
- Yapı değişkeni bildirimleri diziler için başlatıcılar veya başlangıç boyutları belirtemez; sınıf değişkeni bildirimleri olabilir.  
  
- Yapılar <xref:System.ValueType?displayProperty=nameWithType> sınıfından dolaylı olarak devralınır ve diğer herhangi bir türden devralınabilir; sınıflar, <xref:System.ValueType?displayProperty=nameWithType>dışındaki herhangi bir sınıftan veya sınıftan devralınabilir.  
  
- Yapılar devredilemez; sınıflar.  
  
- Yapılar hiçbir şekilde sonlandırılmadığından, ortak dil çalışma zamanı (CLR) herhangi bir yapıda <xref:System.Object.Finalize%2A> yöntemi çağırılmaz; sınıflar, kalan etkin bir başvuru olmadığını algıladığında bir sınıftaki <xref:System.Object.Finalize%2A> çağıran çöp toplayıcı (GC) tarafından sonlandırılır.  
  
- Bir yapı için bir Oluşturucu gerekmez; bir sınıf.  
  
- Yapılar yalnızca parametre alıyorsa paylaşılmayan oluşturuculara sahip olabilir; sınıflar, parametrelere sahip veya parametresiz olabilir.  
  
 Her yapının parametresiz bir örtük ortak Oluşturucusu vardır. Bu Oluşturucu, tüm yapının veri öğelerini varsayılan değerlerine başlatır. Bu davranışı yeniden tanımlayamazsınız.  
  
## <a name="instances-and-variables"></a>Örnekler ve değişkenler  
 Yapılar değer türleri olduğundan, her yapı değişkeni ayrı bir yapı örneğine kalıcı olarak bağlanır. Ancak sınıflar başvuru türleridir ve bir nesne değişkeni farklı zamanlarda çeşitli sınıf örneklerine başvurabilir. Bu ayrım, yapıların ve sınıfların kullanımını aşağıdaki yollarla etkiler:  
  
- **Başlatılmasında.** Yapı değişkeni, yapının parametresiz oluşturucusunu kullanarak örtük olarak öğelerin başlatılmasını içerir. Bu nedenle, `Dim s As struct1` `Dim s As struct1 = New struct1()`eşdeğerdir.  
  
- **Değişkenler atanıyor.** Bir yapı değişkenini diğerine atadığınızda veya bir yapı örneğini bir yordam bağımsız değişkenine geçirdiğinizde, tüm değişken öğelerinin geçerli değerleri yeni yapıya kopyalanır. Bir nesne değişkenini diğerine atadığınızda veya bir yordama bir nesne değişkeni geçirdiğinizde, yalnızca başvuru işaretçisi kopyalanır.  
  
- **Nothing atama.** Bir yapı değişkenine [Nothing](../../../../visual-basic/language-reference/nothing.md) değeri atayabilirsiniz, ancak örnek değişkenle ilişkilendirilmeye devam eder. Kendi yöntemlerini çağırabilirsiniz ve veri öğelerine erişebilirsiniz, ancak değişken öğeleri atama tarafından yeniden başlatılır.  
  
     Buna karşılık, `Nothing`için bir nesne değişkeni ayarlarsanız, herhangi bir sınıf örneğinden ilişkiyi kaldırın ve başka bir örnek yapana kadar değişken aracılığıyla herhangi bir üyeye erişemezsiniz.  
  
- **Birden çok örnek.** Bir nesne değişkeni farklı zamanlarda kendisine atanmış farklı sınıf örneklerine sahip olabilir ve çeşitli nesne değişkenleri aynı anda aynı sınıf örneğine başvurabilir. Sınıf üyeleri değerlerinde yaptığınız değişiklikler, aynı örneğe işaret eden başka bir değişken aracılığıyla erişildiğinde bu üyeleri etkiler.  
  
     Ancak yapı öğeleri kendi örnekleri içinde yalıtılmıştır. Değerlerinde yapılan değişiklikler aynı `Structure` bildiriminin diğer örneklerinde bile diğer herhangi bir yapı değişkenine yansıtılmaz.  
  
- **Eþit.** İki yapının eşitlik testi, öğe öğesi testi ile gerçekleştirilmelidir. İki nesne değişkeni <xref:System.Object.Equals%2A> yöntemi kullanılarak karşılaştırılabilir. <xref:System.Object.Equals%2A> iki değişkenin aynı örneğe işaret edip etmediğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Yapılar ve Diğer Programlama Öğeleri](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Nesneler ve Sınıflar](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
