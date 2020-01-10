---
title: Çok biçimlilik- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 4f65082ad5094eb0aab28edeb06790a9af4019c6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714726"
---
# <a name="polymorphism-c-programming-guide"></a>Çok Biçimlilik (C# Programlama Kılavuzu)
Çok biçimlilik, kapsülleme ve devralma sonrasında nesne odaklı programlama için genellikle üçüncü olarak adlandırılır. Çok biçimlilik, "çoktan şekillendirilmiş" anlamına gelen ve iki ayrı yönü bulunan bir Yunan kelimedir:  
  
- Çalışma zamanında, türetilmiş bir sınıfın nesneleri Yöntem parametreleri ve koleksiyonlar ya da diziler gibi yerlerde bir temel sınıfın nesneleri olarak kabul edilebilir. Bu gerçekleştiğinde, nesnenin bildirildiği tür artık çalışma zamanı türüyle aynı değildir.  
  
- Temel sınıflar [sanal](../../language-reference/keywords/virtual.md) *yöntemleri*tanımlayabilir ve uygulayabilir ve türetilmiş sınıflar bunları [geçersiz kılabilir](../../language-reference/keywords/override.md) , bu da kendi tanım ve uygulamasını sağlar. Çalışma zamanında, istemci kodu yöntemi çağırdığında, CLR nesnenin çalışma zamanı türünü arar ve sanal yöntemin geçersiz kılmasını çağırır. Bu nedenle, kaynak kodunuzda bir yöntemi temel sınıf üzerinde çağırabilir ve türetilmiş sınıfın yönteminin yürütülmesine neden olabilirsiniz.  
  
 Sanal yöntemler, ilişkili nesneler gruplarıyla tek bir şekilde çalışmanıza olanak sağlar. Örneğin, bir kullanıcının çizim yüzeyinde çeşitli şekil türlerini oluşturmalarına olanak tanıyan bir çizim uygulamanız olduğunu varsayalım. Kullanıcı tarafından oluşturulacak belirli şekil türlerini derleme sırasında bilemezsiniz. Bununla birlikte, uygulamanın oluşturulan çeşitli şekil türlerini izlemesi gerekir ve Kullanıcı fare eylemlerine yanıt olarak onları güncelleştirmek zorunda olur. Bu sorunu çözmek için iki temel adımda çok biçimlilik kullanabilirsiniz:  
  
1. Her belirli şekil sınıfının ortak bir temel sınıftan türetildiği bir sınıf hiyerarşisi oluşturun.  
  
2. Temel sınıf yöntemine tek bir çağrı aracılığıyla herhangi bir türetilmiş sınıfta uygun yöntemi çağırmak için bir sanal yöntem kullanın.  
  
 İlk olarak, `Shape`adlı bir temel sınıf ve `Rectangle`, `Circle`ve `Triangle`gibi türetilmiş sınıflar oluşturun. `Shape` sınıfına `Draw`adlı sanal bir yöntem verin ve sınıfın temsil ettiği belirli şekli çizmek için her türetilmiş sınıfta bunu geçersiz kılın. `List<Shape>` nesne oluşturun ve buna bir daire, üçgen ve dikdörtgen ekleyin. Çizim yüzeyini güncelleştirmek için, listeyi yinelemek ve listedeki her bir `Shape` nesnesinde `Draw` yöntemini çağırmak için bir [foreach](../../language-reference/keywords/foreach-in.md) döngüsü kullanın. Listedeki her bir nesne, belirtilen `Shape`türüne sahip olsa da, çağrılacak çalışma zamanı türüdür (her türetilmiş sınıfta yönteminin geçersiz kılınan sürümü).  
  
 [!code-csharp[csProgGuideInheritance#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#50)]  
  
 ' C#De, Kullanıcı tanımlı türler dahil olmak üzere tüm türler <xref:System.Object>' den devraldığı için her tür polimorfik olur.  
  
## <a name="polymorphism-overview"></a>Çok biçimlilik genel bakış  
  
### <a name="virtual-members"></a>Sanal Üyeler  
 Türetilmiş bir sınıf temel sınıftan devraldığında, temel sınıfın tüm yöntemlerini, alanlarını, özelliklerini ve olaylarını alır. Türetilmiş sınıfın Tasarımcısı şunları yapıp oluşturulmayacağını seçebilir  
  
- taban sınıftaki sanal üyeleri geçersiz kıl,  
  
- En yakın temel sınıf yöntemini geçersiz kılmadan devralma  
  
- temel sınıf uygulamalarını gizleyen bu üyelerin sanal olmayan yeni uygulamasını tanımlayın  
  
 Türetilmiş bir sınıf, yalnızca temel sınıf üyesi [sanal](../../language-reference/keywords/virtual.md) veya [soyut](../../language-reference/keywords/abstract.md)olarak bildirilirse bir temel sınıf üyesini geçersiz kılabilir. Türetilmiş üye, metodun sanal çağrıya katılmayı amaçladığı kesin olarak belirtmek için [override](../../language-reference/keywords/override.md) anahtar sözcüğünü kullanmalıdır. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#20)]  
  
 Alanlar sanal olamaz; yalnızca Yöntemler, özellikler, olaylar ve Dizin oluşturucular sanal olabilir. Türetilmiş bir sınıf sanal üyeyi geçersiz kıldığında, bu üye, bu sınıfın bir örneği temel sınıfın bir örneği olarak erişildiği zaman bile çağırılır. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#21)]  
  
 Sanal yöntemler ve özellikler, türetilmiş sınıfların bir yöntemin temel sınıf uygulamasını kullanmaya gerek kalmadan bir temel sınıfı genişletmesine imkan tanır. Daha fazla bilgi için bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](./versioning-with-the-override-and-new-keywords.md). Bir arabirim, bir yöntemi veya uygulamasının türetilmiş sınıflara ayrılmakta olduğu yöntemler kümesini tanımlamak için başka bir yol sağlar. Daha fazla bilgi için bkz. [arabirimler](../interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Temel sınıf üyelerini yeni üyelerle gizleme  
 Türetilmiş üyenin bir temel sınıftaki üye ile aynı ada sahip olmasını istiyorsanız, ancak sanal çağrıya katılmasını istemiyorsanız, [New](../../language-reference/keywords/new-modifier.md) anahtar sözcüğünü kullanabilirsiniz. `new` anahtar sözcüğü, değiştirilmekte olan bir sınıf üyesinin dönüş türünden önce konur. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#18)]  
  
 Gizli temel sınıf üyelerine, türetilmiş sınıfın örneğini bir temel sınıfın örneğine aktararak istemci kodundan de erişilebilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#19)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Türetilmiş sınıfların sanal üyeleri geçersiz kılmasını önler  
 Sanal üyeler ve ilk olarak onu tanımlayan sınıf arasında kaç sınıf bildirildiği bağımsız olarak sanal Üyeler sanal olarak kalır. Sınıf A bir sanal üye bildirirse ve B sınıfı bir ' dan türetilir ve C sınıfı B 'den türetilmişse, C sınıfı sanal üyeyi devralır ve B sınıfı bu üye için bir geçersiz kılma bildirdiğine bakılmaksızın onu geçersiz kılma seçeneğine sahiptir. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#22)]  
  
 Türetilmiş bir sınıf, bir geçersiz kılma [korumalı](../../language-reference/keywords/sealed.md)olarak bildirerek sanal devralmayı durdurabilir. Bu, sınıf üye bildiriminde `override` anahtar sözcüğünden önce `sealed` anahtar sözcüğünü yerleştirmeyi gerektirir. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#24)]  
  
 Önceki örnekte, yöntem `DoWork` artık C 'den türetilmiş hiçbir sınıfta sanal değildir. B türüne veya tür A 'ya dönüştürülseler bile, C örnekleri için hala sanal bir. Sealed yöntemleri, aşağıdaki örnekte gösterildiği gibi, `new` anahtar sözcüğü kullanılarak türetilmiş sınıflar tarafından değiştirilebilir:  
  
 [!code-csharp[csProgGuideInheritance#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#25)]  
  
 Bu durumda, d üzerinde `DoWork`, D türünde bir değişken kullanılarak çağrılırsa, yeni `DoWork` çağırılır. C, B veya A türündeki bir değişken D örneğine erişmek için kullanılırsa, `DoWork` çağrısı, sanal devralma kurallarını izleyerek bu çağrıları C sınıfında `DoWork` uygulamasına yönlendirirsiniz.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Türetilmiş sınıflardan temel sınıf sanal üyelerine erişme  
 Bir yöntemi veya özelliği değiştirilmiş veya geçersiz kılan türetilmiş bir sınıf, `base` anahtar sözcüğünü kullanarak temel sınıftaki yönteme veya özelliğe erişmeye devam edebilir. Aşağıdaki kod bir örnek sağlar:  
  
 [!code-csharp[csProgGuideInheritance#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#26)]  
  
 Daha fazla bilgi için bkz. [Base](../../language-reference/keywords/base.md).  
  
> [!NOTE]
> Sanal üyelerin, kendi uygulamalarında bu üyenin temel sınıf uygulamasını çağırmak için `base` kullanması önerilir. Temel sınıf davranışının oluşmasına izin vermek, türetilmiş sınıfın türetilmiş sınıfa özgü davranış uygulamaya odaklanmalarını sağlar. Temel sınıf uygulama çağrılıp, davranışını temel sınıfın davranışıyla uyumlu hale getirmek için türetilmiş sınıfa kadar olur.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](./versioning-with-the-override-and-new-keywords.md)  
  
- [Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme](./knowing-when-to-use-override-and-new-keywords.md)  
  
- [ToString yöntemini geçersiz kılma](./how-to-override-the-tostring-method.md)
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Devralma](./inheritance.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](./abstract-and-sealed-classes-and-class-members.md)
- [Yöntemler](./methods.md)
- [Olaylar](../events/index.md)
- [Veri Erişimi](./properties.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Türler](../types/index.md)
