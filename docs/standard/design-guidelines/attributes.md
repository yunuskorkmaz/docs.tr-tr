---
title: '{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}'
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: ff38cfdc228fd1eae1ace734ed2688c62c66499a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709562"
---
# <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}
<xref:System.Attribute?displayProperty=nameWithType>, özel öznitelikler tanımlamak için kullanılan bir temel sınıftır.  
  
 Öznitelikler, derlemeler, türler, Üyeler ve parametreler gibi programlama öğelerine eklenebilen ek açıklamalardır. Bunlar derlemenin meta verilerinde depolanır ve yansıma API 'Leri kullanılarak çalışma zamanında erişilebilir. Örneğin, çerçeve tür veya üyenin kullanım dışı olduğunu göstermek için bir türe veya üyeye uygulanabilen <xref:System.ObsoleteAttribute>tanımlar.  
  
 Öznitelikler, özniteliğiyle ilgili ek verileri taşıyan bir veya daha fazla özelliğe sahip olabilir. Örneğin, `ObsoleteAttribute`, bir tür veya üyenin kullanım dışı aldığı sürüm ve eski API 'YI değiştiren yeni API 'lerin açıklaması hakkında ek bilgiler taşıyabilir.  
  
 Özniteliği uygulandığında bir özniteliğin bazı özelliklerinin belirtilmesi gerekir. Bunlar, konumsal Oluşturucu parametreleri olarak temsil edildiği için gereken özellikler veya gerekli bağımsız değişkenler olarak adlandırılır. Örneğin, <xref:System.Diagnostics.ConditionalAttribute> <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> özelliği gerekli bir özelliktir.  
  
 Özniteliği uygulandığında belirtilmesi gereken özellikler isteğe bağlı Özellikler (veya isteğe bağlı bağımsız değişkenler) olarak adlandırılır. Bunlar ayarlanabilir özelliklerle temsil edilir. Derleyiciler, bir öznitelik uygulandığında bu özellikleri ayarlamak için özel söz dizimi sağlar. Örneğin <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özelliği, isteğe bağlı bir bağımsız değişkeni temsil eder.  
  
 **✓ DO** "Özniteliği" soneki ile özel öznitelik sınıfları adı  
  
 **✓ DO** uygulamak <xref:System.AttributeUsageAttribute> özel öznitelikleri için.  
  
 **✓ DO** isteğe bağlı bağımsız değişkeni için ayarlanabilir özellikler sağlar.  
  
 **✓ DO** yalnızca get özellikler için gerekli bağımsız değişkenleri sağlayın.  
  
 **✓ DO** gerekli bağımsız değişkenleri karşılık gelen özellikleri başlatmak için Oluşturucusu parametreleri sağlayın. Her parametrenin karşılık gelen özellik olarak aynı ada sahip olması gerekir (büyük/küçük harfe karşın).  
  
 **X AVOID** Oluşturucu parametreleri için isteğe bağlı bağımsız değişkenleri karşılık gelen özellikleri başlatmak için sağlama.  
  
 Diğer bir deyişle, hem Oluşturucu hem de ayarlayıcı ile ayarlanabilir özellikleri yoktur. Bu kılavuz, hangi bağımsız değişkenlerin isteğe bağlı ve gerekli olduğunu ve aynı şeyi yapmanın iki yolu olmasını engeller.  
  
 **X AVOID** özel öznitelik oluşturucuların aşırı yüklemesi.  
  
 Yalnızca bir oluşturucunun, bağımsız değişkenlerin gerekli olduğu ve isteğe bağlı olduğu kullanıcıya açıkça iletişim kurduğu.  
  
 **✓ DO** özel öznitelik sınıfları, mümkünse korumaya. Bu, özniteliğe yönelik arama işlemini daha hızlı hale getirir.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
