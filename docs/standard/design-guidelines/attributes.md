---
title: Attributes1
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 7ab499d5a9c8388e9081a07921d3e444c0cdd879
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131436"
---
# <a name="attributes"></a>Öznitelikler
<xref:System.Attribute?displayProperty=nameWithType> bir temel sınıf özel öznitelikler tanımlamak için kullanılır.  
  
 Derlemeleri, türleri, üyeler ve parametreler gibi programlama öğelerine eklenebilir ek açıklamaları öznitelikleridir. Bunlar, derlemenin meta verilerde depolanan ve yansıma API'leri kullanarak çalışma zamanında erişilebilir. Örneğin, Framework tanımlar <xref:System.ObsoleteAttribute>, hangi uygulanabilir türe veya üyeye onaylanmaz belirtmek için bir tür veya üye.  
  
 Öznitelikleri, öznitelik için ilgili ek veri taşıyan bir veya daha fazla özelliklere sahip olabilir. Örneğin, `ObsoleteAttribute` sürümde hakkında ek bilgi gerçekleştirmek bir tür veya üye kullanımdan ve eski API değiştirerek yeni API'leri açıklaması.  
  
 Bazı özellikler bir özniteliğin öznitelik uygulandığı zaman belirtilmesi gerekir. Konumsal Oluşturucu parametresi olarak temsil edilir çünkü bunlar için gerekli özellikler veya gerekli bağımsız adlandırılır. Örneğin, <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> özelliği <xref:System.Diagnostics.ConditionalAttribute> gerekli bir özelliktir.  
  
 Mutlaka öznitelik uygulandığında belirtilmesi gerekmez özellikleri, isteğe bağlı özellikleri (veya isteğe bağlı bağımsız değişkenler) adı verilir. Bunlar, ayarlanabilir özelliklerin tarafından temsil edilir. Derleyiciler, bir öznitelik uygulandığında, bu özellikleri ayarlamak için özel bir sözdizimi sağlar. Örneğin, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özelliği, isteğe bağlı bir bağımsız değişkeni temsil eder.  
  
 **✓ DO** "Özniteliği" soneki ile özel öznitelik sınıfları adı  
  
 **✓ DO** uygulamak <xref:System.AttributeUsageAttribute> özel öznitelikleri için.  
  
 **✓ DO** isteğe bağlı bağımsız değişkeni için ayarlanabilir özellikler sağlar.  
  
 **✓ DO** yalnızca get özellikler için gerekli bağımsız değişkenleri sağlayın.  
  
 **✓ DO** gerekli bağımsız değişkenleri karşılık gelen özellikleri başlatmak için Oluşturucusu parametreleri sağlayın. Her parametre karşılık gelen özellik olarak (farklı büyük/küçük harf olsa da ile) aynı adı olmalıdır.  
  
 **X AVOID** Oluşturucu parametreleri için isteğe bağlı bağımsız değişkenleri karşılık gelen özellikleri başlatmak için sağlama.  
  
 Diğer bir deyişle, bir oluşturucu hem de ayarlayıcı ile ayarlanabilir özellikleri yok. Bu kılavuz, hangi bağımsız değişken isteğe bağlıdır ve gerekli olan ve aynı şeyi yapmanın iki yolu zorunluluğunu ortadan çok açık hale getirir.  
  
 **X AVOID** özel öznitelik oluşturucuların aşırı yüklemesi.  
  
 Açıkça yalnızca bir oluşturucuya sahip kullanıcıya hangi bağımsız değişkenleri gereklidir ve isteğe bağlı olduğu iletişim kurar.  
  
 **✓ DO** özel öznitelik sınıfları, mümkünse korumaya. Bu öznitelik için arama daha hızlı sağlar.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
