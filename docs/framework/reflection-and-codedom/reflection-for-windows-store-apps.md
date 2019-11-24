---
title: Windows Mağazası Uygulamaları için .NET Framework'te Yansıma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9aaec282fda0a038d14f3a0cd57e1a8a2855f2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448136"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Windows Mağazası Uygulamaları için .NET Framework'te Yansıma

Starting with the .NET Framework 4.5, the .NET Framework includes a set of reflection types and members for use in Windows 8.x Store apps. These types and members are available in the full .NET Framework as well as in the .NET for Windows Store apps. Bu belge, bunlar ile .NET Framework 4 ve daha önceki sürümlerdeki karşılıkları arasındaki temel farkları açıklar.  
  
 If you are creating a Windows 8.x Store app, you must use the reflection types and members in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Bu türler ve üyeler, gerekli olmasa da aynı zamanda masaüstü uygulamalarında kullanılmak üzere mevcuttur, bu nedenle her iki uygulama türü için de aynı kodu kullanabilirsiniz.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo ve Derleme Yükleme  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]'de, <xref:System.Reflection.TypeInfo> sınıfı .NET Framework 4 <xref:System.Type> sınıfının bazı işlevlerini içerir. Bir <xref:System.Type> nesnesi, tür tanımını kendisi temsil ederken bir <xref:System.Reflection.TypeInfo> nesnesi, tür tanımına bir başvuruyu temsil eder. Bu, başvurdukları derlemenin çalışma zamanı tarafından yüklenmesine gerek olmadan <xref:System.Type> nesnelerini işlemenizi sağlar. İlişkili <xref:System.Reflection.TypeInfo> nesnesini almak, derlemeyi yüklenmeye zorlar.  
  
 <xref:System.Reflection.TypeInfo>, <xref:System.Type>'da kullanılabilir olan üyelerin birçoğunu içerir ve [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]'deki yansıma özelliklerinin birçoğu <xref:System.Reflection.TypeInfo> nesnesinin koleksiyonlarını döndürür. Bir <xref:System.Reflection.TypeInfo> nesnesinden <xref:System.Type> nesnesini almak için <xref:System.Reflection.IReflectableType.GetTypeInfo%2A> yöntemini kullanın.  
  
## <a name="query-methods"></a>Query Methods  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]'da, dizileri döndüren yöntemler yerine <xref:System.Collections.Generic.IEnumerable%601> öğesini döndüren yansıma özelliklerini kullanın. Yansıma bağlamları, büyük derlemeler veya türler için bu koleksiyonların yavaş çapraz geçişini uygulayabilir.  
  
 Yansıma özellikleri, özel bir nesne için, kalıtım ağacına dönmek yerince yalnızca belirtilen yöntemleri kullanırlar. Ayrıca, filtreleme için <xref:System.Reflection.BindingFlags> parametrelerini kullanmaz. Bunun yerine filtreleme işlemi, döndürülen koleksiyonlarda LINQ sorguları kullanılarak kullanıcı kodu içinde yer alır. Çalışma zamanıyla oluşan yansıma nesneleri için (örneğin, `typeof(Object)`'in sonucu olarak) devralma ağacının çapraz geçişi en iyi, <xref:System.Reflection.RuntimeReflectionExtensions> sınıfının yardımcı yöntemleri kullanılarak gerçekleştirilir. Özelleştirilmiş yansıma bağlamlarından gelen nesnelerin tüketicileri bu yöntemleri kullanamaz ve kendileri devralma ağacını kendileri geçirmeleri gerekir.  
  
## <a name="restrictions"></a>Kısıtlamalar  
 In a Windows 8.x Store app, access to some .NET Framework types and members is restricted. Örneğin, bir [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] nesnesini kullanarak, <xref:System.Reflection.MethodInfo>'a dahil edilmeyen .NET Framework yöntemlerini çağıramazsınız. In addition, certain types and members that are not considered safe within the context of a Windows 8.x Store app are blocked, as are <xref:System.Runtime.InteropServices.Marshal> and <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> members. Bu kısıtlama yalnızca .NET Framework türlerini ve üyelerini etkiler; normalde yaptığınız gibi kodunuzu veya üçüncü taraf kodunu çağırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, devralınan yöntemler ve özellikler dahil olmak üzere [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] türünün yöntemlerini ve özelliklerini almak için <xref:System.Globalization.Calendar> öğesinde yansıma türlerini ve üyelerini kullanır. To run this code, paste it into the code file for a Windows 8.x Store page that contains a <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> control named `textblock1` in a project named Reflection. If you paste this code inside a project with a different name, just make sure you change the namespace name to match your project.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yansıma](reflection.md)
