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
ms.openlocfilehash: fb537950ce240d77282551f847b637a77792a264
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645242"
---
# <a name="accessing-custom-attributes"></a>Özel Özniteliklere Erişim
Öznitelikleri program öğelerle ilişkili eklendikten sonra yansıma olmaları ve uygulanmaları değerlerini sorgulamak için kullanılabilir. .NET Framework 1.0 ve 1.1 sürümlerinde, özel öznitelikler yürütme bağlamında incelenir. .NET Framework 2.0 sürümünde yeni bir yükleme bağlamı, yürütme için yüklenemiyor kodu incelemek için kullanılan salt yansıma bağlam sağlar.  
  
## <a name="the-reflection-only-context"></a>Yalnızca yansıma bağlamı  
 Salt yansıma bağlamına yüklenen kodunu yürütülemez. Oluşturucuları yürütülmesi gerekir çünkü bu, özel öznitelikler örneklerini oluşturulamayacağını, anlamına gelir. Yük ve özel öznitelikleri salt yansıma bağlamında incelemek için kullandığınız <xref:System.Reflection.CustomAttributeData> sınıfı. Bu sınıfın örnekleri statik uygun aşırı yüklemesini kullanarak elde edebilirsiniz <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> yöntemi. Bkz: [nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## <a name="the-execution-context"></a>Yürütme bağlamı  
 Sorgu yürütme bağlamı özniteliklerle ana yansıma yöntemlerdir <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> ve <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.  
  
 Özel bir öznitelik erişilebilirliğini bağlı olduğu derleme göre denetlenir. Bu, özel öznitelik oluşturucusunun özel özniteliği ekli olduğu derlemedeki bir türe üzerinde bir yöntemi çağırıp çağırmayacağınızı denetimini eşdeğerdir.  
  
 Yöntemler gibi <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> görünürlük ve erişilebilirliği, tür bağımsız değişkeni kontrol edin. Kullanıcı tanımlı tür içeren derlemenin kod türünü kullanarak özel bir öznitelik alabilirsiniz yalnızca **GetCustomAttributes**.  
  
 Aşağıdaki C# tipik bir özel öznitelik tasarım deseni bir örnektir. Bu, çalışma zamanı özel öznitelik yansıma modelini gösterir.  
  
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
  
 Genel özel öznitelik türü için özel öznitelikleri almak çalışma zamanı girişiminde bulunursa <xref:System.ComponentModel.DescriptionAttribute> bağlı **GetLanguage** yöntemi, aşağıdaki eylemleri gerçekleştirir:  
  
1.  Çalışma zamanı denetimleri tür bağımsız değişkeni **DescriptionAttribute** için **Type.GetCustomAttributes**(tür *türü*) herkese açıktır ve bu nedenle görünür ve erişilebilir.  
  
2.  Çalışma zamanı denetimleri kullanıcı tanımlı türe **MyDescriptionAttribute** sınıfından türetilen **DescriptionAttribute** görünür ve erişilebilir **System.Web.DLL**derleme, yönteme bağlı **GetLanguage**().  
  
3.  Çalışma zamanı denetimleri oluşturucusunun **MyDescriptionAttribute** görünür ve erişilebilir **System.Web.DLL** derleme.  
  
4.  Çalışma zamanı oluşturucusunu çağırır **MyDescriptionAttribute** özel öznitelik parametrelerle ve yeni nesne çağırana döner.  
  
 Özel öznitelik yansıma model türünün tanımlandığı derleme dışından kullanıcı tanımlı türlerin örneklerini dışarıya sızmasına neden olabilecek. Bu gibi kullanıcı tanımlı türler örneklerini döndüren üyelerinden sistem Çalışma Zamanı Kitaplığı'nda farklı değildir <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> dizisi döndürme **RuntimeMethodInfo** nesneleri. Bir istemciden bir kullanıcı tanımlı özel öznitelik türü bulan bilgilerini önlemek için türün üyeleri özel olarak tanımlayın.  
  
 Aşağıdaki örnek, özel özniteliklere erişim elde etmek için yansıma kullanarak en temel yolu gösterir.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Yansımayla İlgili Güvenlik Konuları](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
