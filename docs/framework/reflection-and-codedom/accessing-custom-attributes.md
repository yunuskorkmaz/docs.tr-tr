---
title: Özel Özniteliklere Erişim
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aafd1586068dcd7aaf4a72ef5454e3a2698ccd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397097"
---
# <a name="accessing-custom-attributes"></a>Özel Özniteliklere Erişim
Öznitelikleri program öğelerle ilişkili eklendikten sonra yansıma mevcut olmaları ve değerleri sorgulamak için kullanılabilir. .NET Framework sürüm 1.0 ve 1.1'da, özel öznitelikler yürütme bağlamı incelenir. .NET Framework sürüm 2.0, yeni bir yük bağlamı için yürütme yüklenemiyor kodu incelemek için kullanılan salt yansıma bağlamı sağlar.  
  
## <a name="the-reflection-only-context"></a>Yalnızca yansıma bağlamı  
 Yalnızca yansıma bağlamına yüklenen kod yürütülemez. Kendi oluşturucular yürütülmesi gerekir çünkü bu, özel öznitelikler örneklerini oluşturulamayacağını, anlamına gelir. Yük ve salt yansıma bağlamına özel öznitelikleri incelemek için kullanmak <xref:System.Reflection.CustomAttributeData> sınıfı. Statik uygun aşırı yüklemesine kullanarak bu sınıfın örnekleri, edinebilirsiniz <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> yöntemi. Bkz: [nasıl yapılır: salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## <a name="the-execution-context"></a>Yürütme bağlamı  
 Yürütme bağlamı sorgu öznitelikleri için ana yansıma yöntemleri <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> ve <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.  
  
 Özel bir öznitelik erişilebilirliğini ekli olduğu derleme göre denetlenir. Bu, bir tür özel öznitelik bağlı olduğu derlemesindeki bir yöntem özel öznitelik Oluşturucusu çağırıp çağırmayacağınızı denetimini eşdeğerdir.  
  
 Gibi yöntemler <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> görünürlük ve tür bağımsız değişkeni erişilebilirliğini denetleyin. Kullanıcı tanımlı türünü içeren bütünleştirilmiş kod türünü kullanarak özel bir öznitelik alabilir yalnızca **GetCustomAttributes**.  
  
 Aşağıdaki C# tipik özel öznitelik tasarım deseni örnektir. Çalışma zamanı özel öznitelik yansıma modeli gösterilmektedir.  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 Genel özel öznitelik türü için bir özel öznitelikler almak çalışma zamanı girişiminde bulunursa <xref:System.ComponentModel.DescriptionAttribute> bağlı **GetLanguage** yöntemi, aşağıdaki eylemleri gerçekleştirir:  
  
1.  Çalışma zamanı denetleyen tür bağımsız değişkeni **DescriptionAttribute** için **Type.GetCustomAttributes**(türü *türü*) ortaktır ve bu nedenle görünür ve erişilebilir olduğunu.  
  
2.  Çalışma zamanı denetleyen kullanıcı tanımlı tür **MyDescriptionAttribute** öğesinden türetilen **DescriptionAttribute** görünür ve içinde erişilebilir **System.Web.DLL**derleme, yönteme bağlı **GetLanguage**().  
  
3.  Çalışma zamanı denetleyen oluşturucusunun **MyDescriptionAttribute** görünür ve içinde erişilebilir **System.Web.DLL** derleme.  
  
4.  Çalışma zamanı oluşturucusunun çağırır **MyDescriptionAttribute** özel öznitelik parametrelerle ve çağıran için yeni bir nesne döndürür.  
  
 Özel öznitelik yansıma model türünün tanımlandığı derleme dışına kullanıcı tanımlı türler örneklerini sızıntısı. Bu, kullanıcı tanımlı türler örneklerini gibi dönüş üyelerinden çalışma zamanı sistem Kitaplığı'nda farklı değildir <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> bir dizi döndürme **RuntimeMethodInfo** nesneleri. Kullanıcı tanımlı özel öznitelik türü bulan bilgilerini istemciden önlemek için ortak olmayan olması için türün üyeleri tanımlar.  
  
 Aşağıdaki örnek, özel öznitelikler erişmek için yansıma kullanarak en temel yolu gösterir.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Yansımayla İlgili Güvenlik Konuları](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
