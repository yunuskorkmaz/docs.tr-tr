---
title: "Sınıflar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: "40"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37e810fc5a5397a6b9240346ac28505b11b1e817
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="classes-c-programming-guide"></a>Sınıflar (C# Programlama Kılavuzu)
A *sınıfı* değişkenleri diğer türleri, yöntemleri ve olayları bir arada gruplandırma tarafından kendi özel türler oluşturmanızı sağlayan bir yapıdır. Şeması gibi bir sınıftır. Veri ve türü davranışını tanımlar. Sınıf static olarak bildirilmedi, istemci kodu oluşturarak kullanabilmesi *nesneleri* veya *örnekleri* bir değişkene atanır. Değişken kapsamı dışında tüm başvuruları oluncaya kadar bellekte kalır. O anda CLR, atık toplama için uygun olarak işaretler. Sınıf olarak bildirilirse [statik](../../../csharp/language-reference/keywords/static.md), ardından bellekte yalnızca bir kopya var ve istemci kodu yalnızca erişebileceği sınıfın kendisi değil bir *örnek değişkeni*. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Yapılar, destek sınıfları *devralma*, nesne odaklı programlama temel bir özelliğidir. Daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="declaring-classes"></a>Sınıfları Bildirme  
 Sınıfları kullanarak bildirildiğinde [sınıfı](../../../csharp/language-reference/keywords/class.md) anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 `class` Anahtar sözcüğü erişim düzeyi tarafından öncesinde. Çünkü [ortak](../../../csharp/language-reference/keywords/public.md) kullanılan herkes bu sınıftan nesneleri bu durumda, oluşturabilirsiniz. Sınıf adı `class` anahtar sözcüğü. Davranış ve veri tanımlandığı sınıf gövdesi tanımı kalanı var. Alanlar, özellikleri, yöntemleri ve bir sınıf olaylarına topluca denir *sınıfı üyeleri*.  
  
## <a name="creating-objects"></a>Nesne Oluşturma  
 Bazen birbirinin yerine kullanıldığı rağmen sınıf ve nesne farklı noktalardır. Bir sınıf nesne türünü tanımlar, ancak bir nesne değil. Bir nesne sınıfına göre somut bir varlık ve bazen sınıfının bir örneği da adlandırılır.  
  
 Nesneleri kullanarak oluşturulabilir [yeni](../../../csharp/language-reference/keywords/new.md) nesne, temel sınıfın adını ve ardından anahtar sözcüğü şöyle:  
  
 [!code-csharp[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 Sınıfının bir örneği oluşturulduğunda, nesneye bir başvurusu Programcı geri gönderilir. Önceki örnekte, `object1` temel alan bir nesneye bir başvurusu olan `Customer`. Bu başvuru, yeni bir nesneye başvuruyor ancak nesne verileri içermiyor. Aslında, bir nesne başvurusu bir nesnenin oluşturmadan oluşturabilirsiniz:  
  
 [!code-csharp[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 Böyle bir başvuru bir nesneye erişilmeye çalışılırken çalışma zamanında başarısız olacağı için bir nesneye başvuran yok nesne başvuruları bunun gibi oluşturmanızı öneririz yok. Ancak, böyle bir başvuru bir nesne, yeni bir nesne oluşturma veya bu gibi varolan bir nesne atama başvurmak için yapılabilir:  
  
 [!code-csharp[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 Bu kod iki nesne başvuruları oluşturan her ikisi de aynı nesneye başvuruyor. Bu nedenle, herhangi bir değişiklik üzerinden yapılan nesne `object3` içinde sonraki kullanımlarını yansıtılır `object4`. Sınıflara göre nesneleri başvuruya göre adlandırılır çünkü sınıfları başvuru türleri olarak bilinir.  
  
## <a name="class-inheritance"></a>Sınıf Devralma  
 Devralma kullanarak gerçekleştirilir bir *türetme*, bir sınıfın başka bir deyişle, kullanarak bildirilmiş bir *temel sınıfı* aldığı veri ve davranış devralır. Bir taban sınıf, bir iki nokta üst üste ve bu gibi türetilmiş sınıf adı şu temel sınıfın adını ekleyerek belirtilmiştir:  
  
 [!code-csharp[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 Bir sınıf bir taban sınıf bildirir, Oluşturucular dışında temel sınıfın tüm üyeleri devralır.  
  
 C++ C# sınıfı yalnızca doğrudan bir temel sınıfı devralabilirsiniz. Ancak, bir temel sınıf kendisini başka bir sınıftan çünkü bir sınıfın birden çok taban sınıfı devralır dolaylı olarak. Ayrıca, bir sınıfın doğrudan birden fazla arabirimi uygulayabilirsiniz. Daha fazla bilgi için bkz: [arabirimleri](../../../csharp/programming-guide/interfaces/index.md).  
  
 Bir sınıf bildirilebilir [soyut](../../../csharp/language-reference/keywords/abstract.md). Bir Özet sınıf bir imza tanımı ancak uygulaması olan soyut yöntemler içerir. Soyut sınıfların örneği oluşturulamıyor. Soyut yöntemler uygulayan türetilmiş sınıflar yalnızca kullanılabilir. Bunun aksine, bir [korumalı](../../../csharp/language-reference/keywords/sealed.md) sınıfı diğer sınıfların buradan türetebilir izin vermez. Daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
 Sınıf tanımları farklı kaynak dosyalar arasında bölünebilir. Daha fazla bilgi için bkz: [kısmi sınıflar ve yöntemler](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
## <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, tek bir alan, bir yöntem ve bir oluşturucu adlı özel bir yöntem içeren ortak bir sınıf tanımlanır. Daha fazla bilgi için bkz: [oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md). Sınıfının sonra ile örneği `new` anahtar sözcüğü.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Nesne odaklı programlama](../concepts/object-oriented-programming.md)  
 [Çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [Üyeleri](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [Yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Nesneleri](../../../csharp/programming-guide/classes-and-structs/objects.md)
