---
title: Derleme yüklerini çözme
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: edd398cd3e42e23301dcc992093d14d087754e76
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347250"
---
# <a name="resolve-assembly-loads"></a>Derleme yüklerini çözme
.NET, derleme yüklemesi üzerinde daha fazla denetim gerektiren uygulamalar için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayı sağlar. Uygulamanız, bu olayı işleyerek, yük bağlamına normal yoklama yollarının dışından bir derleme yükleyebilir, kaç tane derleme sürümünden hangilerinin yükleneceğini seçebilir, dinamik bir derlemeyi yayarak ve bu şekilde devam edebilir. Bu konu, <xref:System.AppDomain.AssemblyResolve> olayını işlemeye yönelik rehberlik sağlar.  
  
> [!NOTE]
> Yalnızca yansıma bağlamındaki derleme yüklerini çözümlemek için bunun yerine <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> olayını kullanın.  
  
## <a name="how-the-assemblyresolve-event-works"></a>AssemblyResolve olayı nasıl kullanılır?  
 <xref:System.AppDomain.AssemblyResolve> olayı için bir işleyici kaydettiğinizde, çalışma zamanı bir derlemeye ada göre bağlama başarısız olduğunda işleyici çağrılır. Örneğin, kullanıcı kodundan aşağıdaki yöntemleri çağırmak <xref:System.AppDomain.AssemblyResolve> olayının oluşturulmasına neden olabilir:  
  
- İlk bağımsız değişkeni, yüklenecek derlemenin görünen adını temsil eden bir dize olan (yani <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliği tarafından döndürülen dize) bir <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntem aşırı yüklemesi.  
  
- İlk bağımsız değişkeni yüklenecek derlemeyi tanımlayan bir <xref:System.Reflection.AssemblyName> nesnesi olan bir <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi.  
  
- <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi.  
  
- Başka bir uygulama etki alanındaki bir nesneyi örnekleyen bir <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi.  
  
### <a name="what-the-event-handler-does"></a>Olay işleyicisinin yaptığı  
 <xref:System.AppDomain.AssemblyResolve> olayının işleyicisi, yüklenecek derlemenin görünen adını <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özelliğinde alır. İşleyici derleme adını tanımıyorsa, `null` (C#), `Nothing` (Visual Basic) veya `nullptr` (görsel C++) döndürür.  
  
 İşleyici derleme adını tanırsa, isteği karşılayan bir derlemeyi yükleyebilir ve döndürebilir. Aşağıdaki listede bazı örnek senaryolar açıklanmaktadır.  
  
- İşleyici derlemenin bir sürümünün konumunu biliyorsa, <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntemini kullanarak derlemeyi yükleyebilir ve başarılı olursa yüklenen derlemeyi döndürebilir.  
  
- İşleyicinin bayt dizileri olarak depolanan derlemelerin bir veritabanına erişimi varsa, bayt dizisi alan <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemelerinin birini kullanarak bir bayt dizisi yükleyebilir.  
  
- İşleyici dinamik bir derleme üretebilir ve döndürebilir.  
  
> [!NOTE]
> İşleyici, derlemeyi yük bağlamı içine, yük bağlamına veya Bağlamsız olarak yüklemesi gerekir. İşleyici derlemeyi yalnızca yansıma bağlamına <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> yöntemini kullanarak yüklerse, <xref:System.AppDomain.AssemblyResolve> olayını oluşturan yük girişimi başarısız olur.  
  
 Bu, uygun bir derlemeyi döndürecek olay işleyicisinin sorumluluğundadır. İşleyici, <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellik değerini <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> oluşturucusuna geçirerek istenen derlemenin görünen adını ayrıştırabilirler. .NET Framework 4 ' ten başlayarak, işleyici, geçerli isteğin başka bir derlemenin bağımlılığı olup olmadığını anlamak için <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliğini kullanabilir. Bu bilgiler, bağımlılığı karşılayan bir derlemeyi belirlemesine yardımcı olabilir.  
  
 Olay işleyicisi derlemenin farklı bir sürümünü istenen sürümden döndürebilir.  
  
 Çoğu durumda, işleyici tarafından döndürülen derleme, işleyicinin onu içine yüklediği bağlamdan bağımsız olarak yükleme bağlamında görünür. Örneğin, işleyici bir derlemeyi yük-from bağlamına yüklemek için <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemini kullanıyorsa, işleyici onu döndürdüğünde, derleme yükleme bağlamında görüntülenir. Ancak, aşağıdaki örnekte, işleyici onu döndürdüğünde derleme bağlam olmadan görünür:  
  
- İşleyici bağlamı olmayan bir derlemeyi yükler.  
  
- <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği null değil.  
  
- İstekte bulunan derleme (yani, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği tarafından döndürülen derleme), bağlam olmadan yükleniydi.  
  
 Bağlamlar hakkında bilgi için <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesi ' ne bakın.  
  
 Aynı derlemenin birden çok sürümü aynı uygulama etki alanına yüklenebilir. Tür atama sorunlarına yol açabildiğinden bu uygulama önerilmez. Bkz. [derleme yüklemesi Için en iyi uygulamalar](../../framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Olay işleyicisinin yapması gereken  
<xref:System.AppDomain.AssemblyResolve> olayını işlemeye yönelik birincil kural, tanımadığınız bir derlemeyi döndürmeye çalışmayın. İşleyiciyi yazdığınızda hangi derlemelerin olay oluşturulmasına neden olabileceğini bilmeniz gerekir. İşleyiciniz diğer derlemeler için null değer döndürmelidir.  

> [!IMPORTANT]
> .NET Framework 4 ' ten başlayarak, <xref:System.AppDomain.AssemblyResolve> olayı uydu derlemeleri için oluşturulur. Bu değişiklik, işleyici tüm derleme yükleme isteklerini çözümlemeye çalışırsa .NET Framework önceki bir sürümü için yazılmış bir olay işleyicisini etkiler. Tanımadığı derlemeleri yoksaymayan olay işleyicileri bu değişiklikten etkilenmez: null döndürür ve normal geri dönüş mekanizmaları izlenir.  

Bir derlemeyi yüklerken, olay işleyicisi bir yığın taşmasına yol açabileceğinden, <xref:System.AppDomain.AssemblyResolve> olayının yinelemeli olarak oluşturulmasına neden olabilecek <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemelerinin hiçbirini kullanamaz. (Bu konunun önceki kısımlarında sunulan listeye bakın.) Tüm olay işleyicileri döndürülünceye kadar hiçbir özel durum oluşturulmadığından, yükleme isteği için özel durum işleme sağlıyorsanız bile bu durum oluşur. Bu nedenle, `MyAssembly` bulunamazsa aşağıdaki kod yığın taşmasına neden olur:  

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
