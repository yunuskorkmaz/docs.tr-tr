---
title: Derleme yüklerini çözümle
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: ee9ce292b18c75893dae46582dc5bb966981a614
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973126"
---
# <a name="resolve-assembly-loads"></a>Derleme yüklerini çözümle
.Net, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> derleme yüklemesi üzerinde daha fazla denetim gerektiren uygulamalar için olayı sağlar. Uygulamanız, bu olayı işleyerek, yük bağlamına normal yoklama yollarının dışından bir derleme yükleyebilir, kaç tane derleme sürümünden hangilerinin yükleneceğini seçebilir, dinamik bir derlemeyi yayarak ve bu şekilde devam edebilir. Bu konu, <xref:System.AppDomain.AssemblyResolve> olayı işlemeye yönelik rehberlik sağlar.  
  
> [!NOTE]
> Yalnızca yansıma bağlamındaki derleme yüklerini çözümlemek için, bunun yerine <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> olayını kullanın.  
  
## <a name="how-the-assemblyresolve-event-works"></a>AssemblyResolve olayı nasıl kullanılır?  
 <xref:System.AppDomain.AssemblyResolve> Olay için bir işleyici kaydettiğinizde, çalışma zamanı bir derlemeye ada göre bağlama başarısız olduğunda işleyici çağrılır. Örneğin, aşağıdaki yöntemleri kullanıcı kodundan çağırmak <xref:System.AppDomain.AssemblyResolve> olayın oluşturulmasına neden olabilir:  
  
- İlk bağımsız değişkeni, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yüklenecek derlemenin görünen adını temsil eden bir dize olan bir <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntem aşırı yüklemesi veya yöntem aşırı yüklemesi (yani, özelliği tarafından döndürülen dize).  
  
- İlk bağımsız değişkeni yüklenecek <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> derlemeyi tanımlayan bir nesne olan bir <xref:System.Reflection.AssemblyName> yöntem aşırı yüklemesi veya yöntem aşırı yüklemesi. <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- Bir <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntem aşırı yüklemesi.  
  
- Başka <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> bir <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> uygulama etki alanındaki bir nesneyi örnekleyen bir veya yöntem aşırı yüklemesi.  
  
### <a name="what-the-event-handler-does"></a>Olay işleyicisinin yaptığı  
 <xref:System.AppDomain.AssemblyResolve> Olay işleyicisi, <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özelliğindeki, yüklenecek derlemenin görünen adını alır. İşleyici `null` derleme adını tanımıyorsa, (C#) `Nothing` , (Visual Basic) veya `nullptr` (görsel C++) döndürür.  
  
 İşleyici derleme adını tanırsa, isteği karşılayan bir derlemeyi yükleyebilir ve döndürebilir. Aşağıdaki listede bazı örnek senaryolar açıklanmaktadır.  
  
- İşleyici derlemenin bir sürümünün konumunu biliyorsa, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntemini kullanarak derlemeyi yükleyebilir ve başarılı olursa yüklenen derlemeyi döndürebilir.  
  
- İşleyicinin bayt dizileri olarak depolanan derlemelerin bir veritabanına erişimi varsa, bir bayt dizisi alan aşırı yüklerden birini <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> kullanarak bir bayt dizisi yükleyebilir.  
  
- İşleyici dinamik bir derleme üretebilir ve döndürebilir.  
  
> [!NOTE]
> İşleyici, derlemeyi yük bağlamı içine, yük bağlamına veya Bağlamsız olarak yüklemesi gerekir. İşleyici, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> veya yöntemini kullanarak derlemeyi yalnızca yansıma bağlamına yüklerse, <xref:System.AppDomain.AssemblyResolve> olayı oluşturan yükleme girişimi başarısız olur.  
  
 Bu, uygun bir derlemeyi döndürecek olay işleyicisinin sorumluluğundadır. İşleyici, <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellik değerini <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> oluşturucuya geçirerek, istenen derlemenin görünen adını ayrıştırtırabilir. .NET Framework 4 ' ten başlayarak, işleyici, geçerli isteğin başka <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> bir derlemenin bağımlılığı olup olmadığını bulmak için özelliğini kullanabilir. Bu bilgiler, bağımlılığı karşılayan bir derlemeyi belirlemesine yardımcı olabilir.  
  
 Olay işleyicisi derlemenin farklı bir sürümünü istenen sürümden döndürebilir.  
  
 Çoğu durumda, işleyici tarafından döndürülen derleme, işleyicinin onu içine yüklediği bağlamdan bağımsız olarak yükleme bağlamında görünür. Örneğin, işleyici bir derlemeyi yük-from <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> bağlamına yüklemek için yöntemini kullanıyorsa, işleyici onu döndürdüğünde, derleme yükleme bağlamında görüntülenir. Ancak, aşağıdaki örnekte, işleyici onu döndürdüğünde derleme bağlam olmadan görünür:  
  
- İşleyici bağlamı olmayan bir derlemeyi yükler.  
  
- <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Özellik null değil.  
  
- İstekte bulunan derleme (diğer bir deyişle, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği tarafından döndürülen derleme), bağlamı olmadan yükleniydi.  
  
 Bağlamlar hakkında bilgi için bkz <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> . yöntem aşırı yüklemesi.  
  
 Aynı derlemenin birden çok sürümü aynı uygulama etki alanına yüklenebilir. Tür atama sorunlarına yol açabildiğinden bu uygulama önerilmez. Bkz. [derleme yüklemesi Için en iyi uygulamalar](../../framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Olay işleyicisinin yapması gereken  
<xref:System.AppDomain.AssemblyResolve> Olayı işlemeye yönelik birincil kural, tanımadığınız bir derlemeyi döndürmeye çalışmayın. İşleyiciyi yazdığınızda hangi derlemelerin olay oluşturulmasına neden olabileceğini bilmeniz gerekir. İşleyiciniz diğer derlemeler için null değer döndürmelidir.  

> [!IMPORTANT]
> .NET Framework 4 ' ten başlayarak, <xref:System.AppDomain.AssemblyResolve> etkinlik uydu derlemeleri için oluşturulur. Bu değişiklik, işleyici tüm derleme yükleme isteklerini çözümlemeye çalışırsa .NET Framework önceki bir sürümü için yazılmış bir olay işleyicisini etkiler. Tanımadığı derlemeleri yoksaymayan olay işleyicileri bu değişiklikten etkilenmez: Bunlar null döndürür ve normal geri dönüş mekanizmaları izlenir.  

Bir derlemeyi yüklerken olay işleyicisi, <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.AppDomain.AssemblyResolve> olayın yinelemeli olarak oluşturulmasına neden olabilecek bir veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntem aşırı yüklerini kullanmamalıdır, çünkü bu bir yığın taşmasına yol açabilir. (Bu konunun önceki kısımlarında sunulan listeye bakın.) Tüm olay işleyicileri döndürülünceye kadar hiçbir özel durum oluşturulmadığından, yükleme isteği için özel durum işleme sağlıyorsanız bile bu durum oluşur. Bu nedenle, aşağıdaki kod, bulunmazsa bir yığın taşmasına `MyAssembly` neden olur:  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e) 
    {
        Console::WriteLine("Resolving {0}", e->Name);
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    } 
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        } 
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e) 
    {
        Console.WriteLine("Resolving {0}", e.Name);
        return Assembly.Load(e.Name);
    }
} 

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System
Imports System.Reflection

Class BadExample

    Shared Sub Main()
    
        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yükleme için en iyi uygulamalar](../../framework/deployment/best-practices-for-assembly-loading.md)
- [Uygulama etki alanlarını kullanma](../../framework/app-domains/use.md)
