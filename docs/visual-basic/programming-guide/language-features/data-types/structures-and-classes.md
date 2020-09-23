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
ms.openlocfilehash: e7ca5b9d55611eafad88517e71f9807fe2aa4416
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086224"
---
# <a name="structures-and-classes-visual-basic"></a>Yapılar ve Sınıflar (Visual Basic)

Visual Basic yapılar ve sınıfların sözdizimini birleştirir ve her iki varlığın de aynı özelliklerden çoğunu desteklediği sonuçlardır. Ancak, yapılar ve sınıflar arasında önemli farklılıklar da vardır.  
  
 Sınıfların başvuru türleri olmasının avantajı vardır; bir başvuruyu geçirmek, tüm verileriyle bir yapı değişkeni geçirilmekten daha verimlidir. Diğer yandan, yapılar genel yığında bellek ayırmayı gerektirmez.  
  
 Bir yapıdan kalıtımla almadığı için yapılar yalnızca genişletilmek zorunda olmayan nesneler için kullanılmalıdır. Oluşturmak istediğiniz nesne küçük bir örnek boyutuna sahip olduğunda yapıları kullanın ve sınıfların ve yapıların performans özelliklerini hesaba alın.  
  
## <a name="similarities"></a>Benzerlikler  

 Yapılar ve sınıflar aşağıdaki şekilde benzerdir:  
  
- Her ikisi de *kapsayıcı* türlerdir, yani diğer türleri üye olarak içerirler.  
  
- Her ikisinde de oluşturucular, Yöntemler, özellikler, alanlar, sabitler, numaralandırmalar, olaylar ve olay işleyicilerini içerebilen Üyeler vardır. Ancak, bu üyeleri bir yapının tanımlanmış *öğeleriyle* karıştırmayın.  
  
- Her ikisinin de üyeleri, kişiselleştirilmemiş erişim düzeylerine sahip olabilir. Örneğin, bir üye bildirilebilecek `Public` ve diğeri `Private` .  
  
- Her ikisi de arabirim uygulayabilir.  
  
- Her ikisinde de, parametresiz veya olmayan paylaşılan oluşturucular olabilir.  
  
- Her ikisi de *varsayılan bir özellik*sunabilir, bu özellik en az bir parametre alır.  
  
- Her ikisi de olayları bildirebilir ve oluşturabilir ve her ikisi de temsilciler bildirebilir.  
  
## <a name="differences"></a>Farklılıklar  

 Yapılar ve sınıflar aşağıdaki bununla farklıdır:  
  
- Yapılar *değer türleridir*; sınıflar *başvuru türleridir*. Yapı türünün bir değişkeni, bir sınıf türü olarak veriye bir başvuru eklemek yerine yapının verilerini içerir.  
  
- Yapılar yığın ayırmayı kullanır; sınıflar yığın ayırmayı kullanır.  
  
- Tüm yapı öğeleri `Public` Varsayılan olarak, sınıf değişkenleri ve sabitler varsayılan olarak `Private` , diğer sınıf üyeleri varsayılan olarak kullanılır `Public` . Sınıf üyeleri için bu davranış, varsayılan Visual Basic 6,0 sistemiyle uyumluluk sağlar.  
  
- Bir yapının en az bir paylaşılmayan değişkeni veya paylaşılmayan olmayan, özel olmayan olay öğesi olması gerekir; bir sınıf tamamen boş olabilir.  
  
- Yapı öğeleri olarak bildirilemez `Protected` ; sınıf üyeleri olabilir.  
  
- Bir yapı yordamı yalnızca [paylaşılan](../../../language-reference/modifiers/shared.md) bir `Sub` yordam ve yalnızca [AddHandler ifadesinin](../../../language-reference/statements/addhandler-statement.md)bir yöntemi olduğunda olayları işleyebilir; herhangi bir sınıf yordamı [Handles](../../../language-reference/statements/handles-clause.md) anahtar sözcüğünü veya ifadesini kullanarak olayları işleyebilir `AddHandler` . Daha fazla bilgi için bkz. [Olaylar](../events/index.md).  
  
- Yapı değişkeni bildirimleri diziler için başlatıcılar veya başlangıç boyutları belirtemez; sınıf değişkeni bildirimleri olabilir.  
  
- Yapılar sınıfından dolaylı olarak devralınır <xref:System.ValueType?displayProperty=nameWithType> ve başka herhangi bir türden devralınabilir; sınıflar dışındaki herhangi bir sınıftan veya sınıftan devralınabilir <xref:System.ValueType?displayProperty=nameWithType> .  
  
- Yapılar devredilemez; sınıflar.  
  
- Yapılar hiçbir zaman sonlandırılmadığından, ortak dil çalışma zamanı (CLR) <xref:System.Object.Finalize%2A> herhangi bir yapıda yöntemi çağırılmaz; sınıflar çöp toplayıcı (GC) tarafından sonlandırılır ve <xref:System.Object.Finalize%2A> kalan etkin bir başvuru olmadığını algıladığında bir sınıfa çağrı yapılır.  
  
- Bir yapı için bir Oluşturucu gerekmez; bir sınıf.  
  
- Yapılar yalnızca parametre alıyorsa paylaşılmayan oluşturuculara sahip olabilir; sınıflar, parametrelere sahip veya parametresiz olabilir.  
  
 Her yapının parametresiz bir örtük ortak Oluşturucusu vardır. Bu Oluşturucu, tüm yapının veri öğelerini varsayılan değerlerine başlatır. Bu davranışı yeniden tanımlayamazsınız.  
  
## <a name="instances-and-variables"></a>Örnekler ve değişkenler  

 Yapılar değer türleri olduğundan, her yapı değişkeni ayrı bir yapı örneğine kalıcı olarak bağlanır. Ancak sınıflar başvuru türleridir ve bir nesne değişkeni farklı zamanlarda çeşitli sınıf örneklerine başvurabilir. Bu ayrım, yapıların ve sınıfların kullanımını aşağıdaki yollarla etkiler:  
  
- **Başlatılmasında.** Yapı değişkeni, yapının parametresiz oluşturucusunu kullanarak örtük olarak öğelerin başlatılmasını içerir. Bu nedenle, `Dim s As struct1` ile eşdeğerdir `Dim s As struct1 = New struct1()` .  
  
- **Değişkenler atanıyor.** Bir yapı değişkenini diğerine atadığınızda veya bir yapı örneğini bir yordam bağımsız değişkenine geçirdiğinizde, tüm değişken öğelerinin geçerli değerleri yeni yapıya kopyalanır. Bir nesne değişkenini diğerine atadığınızda veya bir yordama bir nesne değişkeni geçirdiğinizde, yalnızca başvuru işaretçisi kopyalanır.  
  
- **Nothing atama.** Bir yapı değişkenine [Nothing](../../../language-reference/nothing.md) değeri atayabilirsiniz, ancak örnek değişkenle ilişkilendirilmeye devam eder. Kendi yöntemlerini çağırabilirsiniz ve veri öğelerine erişebilirsiniz, ancak değişken öğeleri atama tarafından yeniden başlatılır.  
  
     Buna karşılık, ' a bir nesne değişkeni ayarlarsanız, `Nothing` herhangi bir sınıf örneğinden ilişkiyi kaldırın ve başka bir örnek yapana kadar değişken aracılığıyla herhangi bir üyeye erişemezsiniz.  
  
- **Birden çok örnek.** Bir nesne değişkeni farklı zamanlarda kendisine atanmış farklı sınıf örneklerine sahip olabilir ve çeşitli nesne değişkenleri aynı anda aynı sınıf örneğine başvurabilir. Sınıf üyeleri değerlerinde yaptığınız değişiklikler, aynı örneğe işaret eden başka bir değişken aracılığıyla erişildiğinde bu üyeleri etkiler.  
  
     Ancak yapı öğeleri kendi örnekleri içinde yalıtılmıştır. Değerlerinde yapılan değişiklikler, aynı bildirimin diğer örneklerinde bile diğer herhangi bir yapı değişkenine yansıtılmaz `Structure` .  
  
- **Eþit.** İki yapının eşitlik testi, öğe öğesi testi ile gerçekleştirilmelidir. İki nesne değişkeni, yöntemi kullanılarak karşılaştırılabilir <xref:System.Object.Equals%2A> . <xref:System.Object.Equals%2A> iki değişkenin aynı örneğe işaret edip etmediğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Bileşik Veri Türleri](composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Yapılar](structures.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Yapılar ve Diğer Programlama Öğeleri](structures-and-other-programming-elements.md)
- [Nesneler ve sınıflar](../objects-and-classes/index.md)
