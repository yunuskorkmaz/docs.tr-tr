---
title: Windows Mağazası Uygulamaları için .NET Framework'te Yansıma
description: Windows Mağazası uygulamaları için .NET ' te yansıma kullanın. Windows Mağazası uygulamalarında kullanılmak üzere tüm .NET için kullanılabilen yansıma türleri ve üyeleri kümesi vardır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
ms.openlocfilehash: 86bb633e97f0f88dc2a2a042b6897695a258cc3c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865274"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Windows Mağazası Uygulamaları için .NET Framework'te Yansıma

.NET Framework 4,5 ' den başlayarak, .NET Framework, Windows 8. x Mağaza uygulamalarında kullanılmak üzere bir yansıma türü ve üye kümesi içerir. Bu türler ve Üyeler, Windows Mağazası uygulamaları için .NET içindeki ve tam .NET Framework de mevcuttur. Bu belge, bunlar ile .NET Framework 4 ve daha önceki sürümlerdeki karşılıkları arasındaki temel farkları açıklar.  
  
 Bir Windows 8. x Mağazası uygulaması oluşturuyorsanız, Windows 8. x Mağazası uygulamaları için .NET içindeki yansıma türlerini ve üyelerini kullanmanız gerekir. Bu türler ve üyeler, gerekli olmasa da aynı zamanda masaüstü uygulamalarında kullanılmak üzere mevcuttur, bu nedenle her iki uygulama türü için de aynı kodu kullanabilirsiniz.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo ve Derleme Yükleme  
 Windows 8. x Mağazası uygulamaları için .NET sürümünde, <xref:System.Reflection.TypeInfo> sınıfı .NET Framework 4 sınıfının bazı işlevlerini içerir <xref:System.Type> . Bir <xref:System.Type> nesnesi, tür tanımını kendisi temsil ederken bir <xref:System.Reflection.TypeInfo> nesnesi, tür tanımına bir başvuruyu temsil eder. Bu, başvurdukları derlemenin çalışma zamanı tarafından yüklenmesine gerek olmadan <xref:System.Type> nesnelerini işlemenizi sağlar. İlişkili <xref:System.Reflection.TypeInfo> nesnesini almak, derlemeyi yüklenmeye zorlar.  
  
 <xref:System.Reflection.TypeInfo>üzerinde kullanılabilen birçok üyeyi içerir <xref:System.Type> ve Windows 8. x Mağazası uygulamaları için .NET içindeki yansıma özelliklerinin birçoğu nesne koleksiyonları döndürür <xref:System.Reflection.TypeInfo> . Bir <xref:System.Reflection.TypeInfo> nesnesinden <xref:System.Type> nesnesini almak için <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> yöntemini kullanın.  
  
## <a name="query-methods"></a>Sorgu yöntemleri  
 Windows 8. x Mağazası uygulamaları için .NET sürümünde, <xref:System.Collections.Generic.IEnumerable%601> diziler döndüren yöntemler yerine koleksiyonlar döndüren yansıma özelliklerini kullanırsınız. Yansıma bağlamları, büyük derlemeler veya türler için bu koleksiyonların yavaş çapraz geçişini uygulayabilir.  
  
 Yansıma özellikleri, özel bir nesne için, kalıtım ağacına dönmek yerince yalnızca belirtilen yöntemleri kullanırlar. Ayrıca, filtreleme için <xref:System.Reflection.BindingFlags> parametrelerini kullanmaz. Bunun yerine filtreleme işlemi, döndürülen koleksiyonlarda LINQ sorguları kullanılarak kullanıcı kodu içinde yer alır. Çalışma zamanıyla oluşan yansıma nesneleri için (örneğin, `typeof(Object)`'in sonucu olarak) devralma ağacının çapraz geçişi en iyi, <xref:System.Reflection.RuntimeReflectionExtensions> sınıfının yardımcı yöntemleri kullanılarak gerçekleştirilir. Özelleştirilmiş yansıma bağlamlarından gelen nesnelerin tüketicileri bu yöntemleri kullanamaz ve kendileri devralma ağacını kendileri geçirmeleri gerekir.  
  
## <a name="restrictions"></a>Kısıtlamalar  
 Bir Windows 8. x Mağazası uygulamasında bazı .NET Framework türlerine ve üyelere erişim kısıtlıdır. Örneğin, bir nesnesi kullanarak, Windows 8. x Mağazası uygulamaları için .NET 'e dahil olmayan .NET Framework Yöntemler çağrılamaz <xref:System.Reflection.MethodInfo> . Ayrıca, Windows 8. x Mağazası uygulaması bağlamında güvenli kabul edilmeyen bazı türler ve Üyeler, ve üyeleri olduğu gibi engellenir <xref:System.Runtime.InteropServices.Marshal> <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> . Bu kısıtlama yalnızca .NET Framework türlerini ve üyelerini etkiler; normalde yaptığınız gibi kodunuzu veya üçüncü taraf kodunu çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, Windows 8. x Mağazası uygulamaları için .NET içindeki yansıma türlerini ve üyelerini <xref:System.Globalization.Calendar> , devralınan Yöntemler ve özellikler dahil olmak üzere, türünün yöntemlerini ve özelliklerini almak için kullanır. Bu kodu çalıştırmak için, <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> `textblock1` yansıma adlı bir projede adlı bir denetim Içeren bir Windows 8. x depolama sayfası için kod dosyasına yapıştırın. Bu kodu, farklı bir ada sahip bir proje içine yapıştırırsanız, yalnızca ad alanı adını projenizle eşleşecek şekilde değiştirdiğinizden emin olun.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma](reflection.md)
