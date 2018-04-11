---
title: Sınıflar - C# Kılavuzu
description: Sınıf türleri ve bunları oluşturma hakkında bilgi edinin
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 13cbd3a5b53ea9b0f1acb22684b6a28639d00751
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="classes"></a>Sınıflar
A *sınıfı* değişkenleri diğer türleri, yöntemleri ve olayları bir arada gruplandırma tarafından kendi özel türler oluşturmanızı sağlayan bir yapıdır. Şeması gibi bir sınıftır. Veri ve türü davranışını tanımlar. Sınıf static olarak bildirilmedi, istemci kodu oluşturarak kullanabilmesi *nesneleri* veya *örnekleri* bir değişkene atanır. Değişken kapsamı dışında tüm başvuruları oluncaya kadar bellekte kalır. O anda CLR, atık toplama için uygun olarak işaretler. Sınıf olarak bildirilirse [statik](language-reference/keywords/static.md), ardından bellekte yalnızca bir kopya var ve istemci kodu yalnızca erişebileceği sınıfın kendisi değil bir *örnek değişkeni*. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  

## <a name="reference-types"></a>Başvuru türleri  
Olarak tanımlanan bir tür bir [sınıfı](language-reference/keywords/class.md) olan bir *başvuru türüne*. Ne zaman bildirdiğiniz başvuru türünde bir değişken, çalışma zamanında değişken değeri içeren [null](language-reference/keywords/null.md) açıkça kullanarak nesnesinin örneğini oluşturma kadar [yeni](language-reference/keywords/new.md) işleci, veya bir nesne atama oluşturulan başka bir yerde kullanarak [yeni](language-reference/keywords/new.md), aşağıdaki örnekte gösterildiği gibi:  

[!code-csharp[Reference Types](../../samples/snippets/csharp/concepts/classes/reference-type.cs)]
  
Nesne oluşturulduğunda, bellek yönetilen yığında ayrılan ve yalnızca bir nesnenin konumunu başvuru değişkeni içerir. Yönetilen yığın türlerinde gerektiren ek yükü bunlar ayırırken hem olarak adlandırılıyor CLR otomatik bellek yönetimi işlevselliğini tarafından talep edilen zaman *çöp toplama*. Ancak, atık toplama ayrıca getirilmiş ve çoğu senaryoda, bir performans sorunu oluşturmaz. Çöp toplama hakkında daha fazla bilgi için bkz: [otomatik bellek yönetimi ve çöp toplama](../standard/garbage-collection/gc.md).  
  
Başvuru türleri tam destek *devralma*, nesne odaklı programlama temel bir özelliğidir. Bir sınıf oluşturduğunuzda, herhangi bir arabirim veya olarak tanımlanmamış sınıfı devralabilirsiniz [korumalı](language-reference/keywords/sealed.md), ve diğer sınıflar, sınıfından devralınır ve sanal yöntemleri geçersiz kılın. Daha fazla bilgi için bkz: [devralma](programming-guide/classes-and-structs/inheritance.md).

## <a name="declaring-classes"></a>Sınıfları bildirme  
Sınıfları kullanarak bildirildiğinde [sınıfı](language-reference/keywords/class.md) anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:  
  
[!code-csharp[Declaring Classes](../../samples/snippets/csharp/concepts/classes/declaring-classes.cs)]  
  
**Sınıfı** anahtar sözcüğü tarafından erişim değiştiricisi öncesinde. Çünkü [ortak](language-reference/keywords/public.md) kullanılan herkes bu sınıftan nesneleri bu durumda, oluşturabilirsiniz. Sınıf adı **sınıfı** anahtar sözcüğü. Davranış ve veri tanımlandığı sınıf gövdesi tanımı kalanı var. Alanlar, özellikleri, yöntemleri ve bir sınıf olaylarına topluca denir *sınıfı üyeleri*.  
  
## <a name="creating-objects"></a>Nesne oluşturma  
Bir sınıf nesne türünü tanımlar, ancak bir nesne değil. Bir nesne sınıfına göre somut bir varlık ve bazen sınıfının bir örneği da adlandırılır.  
  
Nesneleri kullanarak oluşturulabilir [yeni](language-reference/keywords/new.md) nesne, temel sınıfın adını ve ardından anahtar sözcüğü şöyle:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects.cs)]   
  
Sınıfının bir örneği oluşturulduğunda, nesneye bir başvurusu Programcı geri gönderilir. Önceki örnekte, `object1` temel alan bir nesneye bir başvurusu olan `Customer`. Bu başvuru, yeni bir nesneye başvuruyor ancak nesne verileri içermiyor. Aslında, bir nesne başvurusu bir nesnenin oluşturmadan oluşturabilirsiniz:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects2.cs)]  
  
Böyle bir başvuru bir nesneye erişilmeye çalışılırken çalışma zamanında başarısız olacağı için bir nesneye başvurmuyor bunun gibi nesne başvuruları oluşturma önermiyoruz. Ancak, böyle bir başvuru bir nesne, yeni bir nesne oluşturma veya bu gibi varolan bir nesne atama başvurmak için yapılabilir:  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects3.cs)]  
  
Bu kod iki nesne başvuruları oluşturan her ikisi de aynı nesneye başvuruyor. Bu nedenle, herhangi bir değişiklik üzerinden yapılan nesne `object3` içinde sonraki kullanımlarını yansıtılır `object4`. Sınıflara göre nesneleri başvuruya göre adlandırılır çünkü sınıfları başvuru türleri olarak bilinir.  
  
## <a name="class-inheritance"></a>Sınıf devralma  
Devralma kullanarak gerçekleştirilir bir *türetme*, bir sınıfın başka bir deyişle, kullanarak bildirilmiş bir *temel sınıfı* aldığı veri ve davranış devralır. Bir taban sınıf, bir iki nokta üst üste ve bu gibi türetilmiş sınıf adı şu temel sınıfın adını ekleyerek belirtilmiştir:  
  
[!code-csharp[Inheritance](../../samples/snippets/csharp/concepts/classes/inheritance.cs)]  
  
Bir sınıf bir taban sınıf bildirir, Oluşturucular dışında temel sınıfın tüm üyeleri devralır.  
  
C++ C# sınıfı yalnızca doğrudan bir temel sınıfı devralabilirsiniz. Ancak, bir temel sınıf kendisini başka bir sınıftan çünkü bir sınıfın birden çok taban sınıfı devralır dolaylı olarak. Ayrıca, bir sınıfın doğrudan birden fazla arabirimi uygulayabilirsiniz. Daha fazla bilgi için bkz: [arabirimleri](programming-guide/interfaces/index.md).  
  
Bir sınıf bildirilebilir [soyut](language-reference/keywords/abstract.md). Bir Özet sınıf bir imza tanımı ancak uygulaması olan soyut yöntemler içerir. Soyut sınıfların örneği oluşturulamıyor. Soyut yöntemler uygulayan türetilmiş sınıflar yalnızca kullanılabilir. Bunun aksine, bir [korumalı](language-reference/keywords/sealed.md) sınıfı diğer sınıfların buradan türetebilir izin vermez. Daha fazla bilgi için bkz: [soyut ve korumalı sınıflar ve sınıf üyeleri](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
Sınıf tanımları farklı kaynak dosyalar arasında bölünebilir. Daha fazla bilgi için bkz: [parçalı sınıf tanımları](programming-guide/classes-and-structs/partial-classes-and-methods.md).  
  
 
## <a name="example"></a>Örnek
Aşağıdaki örnekte, tek bir alan, bir yöntem ve bir oluşturucu adlı özel bir yöntem içeren ortak bir sınıf tanımlanır. Daha fazla bilgi için bkz: [oluşturucular](programming-guide/classes-and-structs/constructors.md). Sınıfının sonra ile örneği **yeni** anahtar sözcüğü.

[!code-csharp[Class Example](../../samples/snippets/csharp/concepts/classes/class-example.cs)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi  
Daha fazla bilgi için bkz: [C# dil belirtimi](language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.  
[C# programlama kılavuzu](programming-guide/index.md)   
[Çok biçimlilik](programming-guide/classes-and-structs/polymorphism.md)   
[Sınıf ve yapı üyeleri](programming-guide/classes-and-structs/members.md)   
[Sınıf ve yapı yöntemleri](programming-guide/classes-and-structs/methods.md)   
[Oluşturucular](programming-guide/classes-and-structs/constructors.md)   
[Sonlandırıcılar](programming-guide/classes-and-structs/destructors.md)   
[Nesneler](programming-guide/classes-and-structs/objects.md)

