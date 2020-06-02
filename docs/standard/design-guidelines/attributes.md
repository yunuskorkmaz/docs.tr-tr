---
title: Öznitelikler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 12a67d75a5f9642408cca69b2e3764a67f101549
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280588"
---
# <a name="attributes"></a>Öznitelikler

<xref:System.Attribute?displayProperty=nameWithType>, özel öznitelikler tanımlamak için kullanılan bir temel sınıftır.

 Öznitelikler, derlemeler, türler, Üyeler ve parametreler gibi programlama öğelerine eklenebilen ek açıklamalardır. Bunlar derlemenin meta verilerinde depolanır ve yansıma API 'Leri kullanılarak çalışma zamanında erişilebilir. Örneğin, .NET, <xref:System.ObsoleteAttribute> tür veya üyenin kullanım dışı olduğunu göstermek için bir türe veya üyeye uygulanabilecek özniteliği tanımlar.

 Öznitelikler, özniteliğiyle ilgili ek verileri taşıyan bir veya daha fazla özelliğe sahip olabilir. Örneğin, `ObsoleteAttribute` bir tür veya üyenin kullanım dışı aldığı ve eskı API 'nin yerini alan yenı API 'nin bir açıklamasıyla ilgili ek bilgiler taşıyabildi.

 Özniteliği uygulandığında bir özniteliğin bazı özelliklerinin belirtilmesi gerekir. Bunlar, konumsal Oluşturucu parametreleri olarak temsil edildiği için gereken özellikler veya gerekli bağımsız değişkenler olarak adlandırılır. Örneğin, <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> öğesinin özelliği <xref:System.Diagnostics.ConditionalAttribute> gerekli bir özelliktir.

 Özniteliği uygulandığında gerekli olmayan özellikler isteğe bağlı Özellikler (veya isteğe bağlı bağımsız değişkenler) olarak adlandırılır. Bunlar ayarlanabilir özelliklerle temsil edilir. Derleyiciler, bir öznitelik uygulandığında bu özellikleri ayarlamak için özel söz dizimi sağlar. Örneğin, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Özellik isteğe bağlı bir bağımsız değişkeni temsil eder.

 ✔️ Özel öznitelik sınıflarını "Attribute" sonekiyle birlikte adlandırın.

 ✔️ <xref:System.AttributeUsageAttribute> özel özniteliklere uygulayın.

 ✔️ isteğe bağlı bağımsız değişkenler için ayarlanabilir özellikler sağlar.

 ✔️ gerekli bağımsız değişkenler için salt al özellikleri sağlar.

 ✔️ gerekli bağımsız değişkenlere karşılık gelen özellikleri başlatmak için Oluşturucu parametreleri sağlar. Her parametrenin karşılık gelen özellik olarak aynı ada sahip olması gerekir (büyük/küçük harfe karşın).

 ❌İsteğe bağlı bağımsız değişkenlere karşılık gelen özellikleri başlatmak için Oluşturucu parametreleri sağlamaktan KAÇıNıN.

 Diğer bir deyişle, hem Oluşturucu hem de ayarlayıcı ile ayarlanabilir özellikleri yoktur. Bu kılavuz, hangi bağımsız değişkenlerin isteğe bağlı ve gerekli olduğunu ve aynı şeyi yapmanın iki yolu olmasını engeller.

 ❌Özel öznitelik oluşturucularını aşırı yüklemeyi ÖNLEYIN.

 Yalnızca bir oluşturucunun, bağımsız değişkenlerin gerekli olduğu ve isteğe bağlı olduğu kullanıcıya açıkça iletişim kurduğu.

 Mümkünse, özel öznitelik sınıflarını mühürlemek ✔️. Bu, özniteliğe yönelik arama işlemini daha hızlı hale getirir.

 *Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Kullanım yönergeleri](usage-guidelines.md)
