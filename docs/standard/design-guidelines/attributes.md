---
title: Attributes1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c169586091f0e7e094e0231f9e247e8907371ec4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="attributes"></a>Öznitelikler
<xref:System.Attribute?displayProperty=nameWithType> bir taban sınıf özel öznitelikleri tanımlamak için kullanılır.  
  
 Derlemeler, türleri, üyeleri ve parametreler gibi programlama öğeleri ile eklenen ek açıklamaları öznitelikleridir. Bunlar derlemesi meta verilerde depolanır ve yansıma API'lerini kullanarak çalışma zamanında erişilebilir. Örneğin, Framework tanımlar <xref:System.ObsoleteAttribute>, hangi uygulanabilir tür veya üye onaylanmaz belirtmek için bir tür veya üye.  
  
 Öznitelikler için öznitelik ilgili ek veri taşımak bir veya daha fazla özelliklere sahip olabilir. Örneğin, `ObsoleteAttribute` sürümde hakkında ek bilgi taşımak, bir tür veya üye kullanımdan ve eski API değiştirerek yeni API açıklaması.  
  
 Öznitelik uygulandığında bir özniteliğin bazı özellikler belirtilmelidir. Konumsal Oluşturucusu parametre olarak temsil edilir çünkü bunlar gerekli özellikleri veya gerekli bağımsız olarak adlandırılır. Örneğin, <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> özelliği <xref:System.Diagnostics.ConditionalAttribute> gerekli bir özelliktir.  
  
 Mutlaka öznitelik olduğunda uygulanır belirtilmesi gerekmez özellikleri isteğe bağlı özellikleri (veya isteğe bağlı bağımsız değişkenler) adı verilir. Bunlar ayarlanabilir özellikleri tarafından gösterilir. Derleyicileri bir öznitelik uygulandığında bu özellikleri ayarlamak için özel bir sözdizimi sağlar. Örneğin, <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> özelliği, isteğe bağlı bir bağımsız değişkeni temsil eder.  
  
 **✓ YAPMAK** "Özniteliği" soneki ile özel öznitelik sınıfları adı  
  
 **✓ YAPMAK** uygulamak <xref:System.AttributeUsageAttribute> özel öznitelikleri için.  
  
 **✓ YAPMAK** isteğe bağlı bağımsız değişkeni için ayarlanabilir özellikler sağlar.  
  
 **✓ YAPMAK** yalnızca get özellikler için gerekli bağımsız değişkenleri sağlayın.  
  
 **✓ YAPMAK** gerekli bağımsız değişkenleri karşılık gelen özellikleri başlatmak için Oluşturucusu parametreleri sağlayın. Her bir parametreyi aynı adı karşılık gelen özelliği (ile farklı büyük/küçük harf rağmen) olmalıdır.  
  
 **KAÇININ x** Oluşturucu parametreleri için isteğe bağlı bağımsız değişkenleri karşılık gelen özellikleri başlatmak için sağlama.  
  
 Diğer bir deyişle, hem bir oluşturucu hem de ayarlayıcı ile ayarlayabileceğiniz özellikleri yok. Bu kılavuz, hangi bağımsız değişkenler isteğe bağlıdır ve hangi gereklidir ve aynı işi yapmanın iki yolu belirlemeyi önler çok açık hale getirir.  
  
 **KAÇININ x** özel öznitelik oluşturucuların aşırı yüklemesi.  
  
 Açıkça sadece bir oluşturucuya sahip kullanıcıya hangi bağımsız değişkenler zorunludur ve isteğe bağlı olduğu iletişim kurar.  
  
 **✓ YAPMAK** özel öznitelik sınıfları, mümkünse korumaya. Bu öznitelik için araması hızlandırır.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
