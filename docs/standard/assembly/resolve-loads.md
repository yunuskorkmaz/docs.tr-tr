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
ms.openlocfilehash: d6314fae266505fbb4410aaaa351973070ab3811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156445"
---
# <a name="resolve-assembly-loads"></a>Derleme yüklerini çözme
.NET, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> montaj yüklemesi üzerinde daha fazla denetim gerektiren uygulamalar için olay sağlar. Bu olayı işleyerek, uygulamanız normal sondalama yollarının dışından bir derlemeyi yükleyebilir, yüklemek için birkaç montaj sürümünden hangisini seçebilir, dinamik bir derleme yontabilir ve döndürebilir ve böylece devam edebilir. Bu <xref:System.AppDomain.AssemblyResolve> konu, olayı işlemek için kılavuz sağlar.  
  
> [!NOTE]
> Yalnızca yansıma bağlamında montaj yüklerini çözmek için <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> olayı kullanın.  
  
## <a name="how-the-assemblyresolve-event-works"></a>AssemblyResolve olayı nasıl çalışır?  
 <xref:System.AppDomain.AssemblyResolve> Olay için bir işleyici kaydettiğinizde, çalışma zamanı ada göre derlemeye bağlanamayınca işleyici çağrılır. Örneğin, kullanıcı kodundan aşağıdaki yöntemleri çağırmak <xref:System.AppDomain.AssemblyResolve> olayın yükseltilmesine neden olabilir:  
  
- İlk <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> bağımsız değişkeni yüklemek için derlemenin görüntü adını temsil eden bir dize olan bir yöntem aşırı yükleme (diğer <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> bir şekilde, <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özellik tarafından döndürülen dize).  
  
- İlk <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> bağımsız değişkeni yüklenmesi için derlemeyi tanımlayan bir nesne olan bir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.AssemblyName> yöntem aşırı yükleme.  
  
- Aşırı <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> bir yöntem.  
  
- Başka <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> bir uygulama etki alanında bir nesneyi anında alan bir veya yöntem aşırı yükleme.  
  
### <a name="what-the-event-handler-does"></a>Olay işleyicisi ne yapar  
 Olayın işleyicisi, <xref:System.AppDomain.AssemblyResolve> <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellikte yüklenecek derlemenin görüntü adını alır. İşleyici derleme adını tanımıyorsa, (C#), `null` `Nothing` (Visual Basic) `nullptr` veya (Visual C++) döndürür.  
  
 İşleyici montaj adını tanırsa, isteği karşılayan bir derleme yükleyebilir ve döndürebilir. Aşağıdaki listede bazı örnek senaryolar açıklanmaktadır.  
  
- İşleyici, derlemenin bir sürümünün konumunu biliyorsa, veya <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntemi kullanarak derlemeyi yükleyebilir ve başarılı olursa yüklenen derlemeyi döndürebilir.  
  
- İşleyici, bayt dizileri olarak depolanan derlemeler veritabanına erişebiliyorsa, bayt dizisini alan <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemin aşırı yüklenmesi yönteminden birini kullanarak bir bayt dizisini yükleyebilir.  
  
- İşleyici dinamik bir derleme oluşturabilir ve döndürebilir.  
  
> [!NOTE]
> Işleyici, derlemeyi yük bağlamına, yük bağlamına veya bağlam olmadan yüklemelidir. Işleyici, derlemeyi <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> yalnızca yansıma bağlamına, <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> yöntemi veya yöntemi kullanarak yüklerse, <xref:System.AppDomain.AssemblyResolve> olayı yükselten yük girişimi başarısız olur.  
  
 Uygun bir derlemeyi döndürmek olay işleyicisinin sorumluluğundadır. İşleyici, <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellik değerini <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> oluşturucuya geçirerek istenen derlemenin görüntü adını ayrıştırabilir. .NET Framework 4'ten başlayarak, işleyici geçerli isteğin başka bir derlemenin bağımlılığı olup olmadığını belirlemek için <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği kullanabilir. Bu bilgiler, bağımlılığı karşılayacak bir derleme belirlemenize yardımcı olabilir.  
  
 Olay işleyicisi, derlemenin istenen sürümden farklı bir sürümünü döndürebilir.  
  
 Çoğu durumda, işleyici tarafından döndürülen derleme, işleyicinin yükettiği bağlamdan bağımsız olarak yük bağlamında görünür. Örneğin, işleyici bir derlemeyi yük ten bağlamına yüklemek için <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi kullanırsa, işleyici onu döndürdüğünde derleme yük bağlamında görünür. Ancak, aşağıdaki durumda işleyici döndürdüğünde derleme bağlamsız görünür:  
  
- Işleyici bağlam olmadan bir derleme yükler.  
  
- Mülk <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> hükümsüz değil.  
  
- İstenen derleme (diğer bir şekilde, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özellik tarafından döndürülen derleme) bağlam olmadan yüklendi.  
  
 Bağlamlar hakkında bilgi için <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> aşırı yükleme yöntemine bakın.  
  
 Aynı derlemenin birden çok sürümü aynı uygulama etki alanına yüklenebilir. Tür atama sorunlarına yol açabileceğinden, bu uygulama önerilmez. [Montaj yüklemesi için en iyi uygulamalara](../../framework/deployment/best-practices-for-assembly-loading.md)bakın.  
  
### <a name="what-the-event-handler-should-not-do"></a>Olay işleyicisinin yapmaması gerekenler  
<xref:System.AppDomain.AssemblyResolve> Olayı işlemek için birincil kural, tanımadığınız bir derlemeyi döndürmeye çalışmamanız gerektiğidir. Işleyiciyi yazarken, hangi derlemelerin olayın yükseltilmesine neden olabileceğini bilmeniz gerekir. Amiriniz diğer derlemeler için null döndürmelidir.  

> [!IMPORTANT]
> .NET Framework 4'ten <xref:System.AppDomain.AssemblyResolve> başlayarak, uydu meclisleri için etkinlik yükseltilir. İşleyici tüm derleme yük isteklerini çözmeye çalışırsa, bu değişiklik .NET Framework'ün önceki bir sürümü için yazılmış bir olay işleyicisini etkiler. Tanımadıkları derlemeleri yok sayan olay işleyicileri bu değişiklikten etkilenmez: Null döndürürler ve normal geri dönüş mekanizmaları izlenir.  

Bir derleme yüklerken, <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.AppDomain.AssemblyResolve> olay işleyicisi olayın yinelemeli olarak yükseltilmesine neden olabilecek aşırı yüklemeleri kullanmamalıdır, çünkü bu bir yığın taşmasına neden olabilir. (Bu konuda daha önce verilen listeye bakın.) Tüm olay işleyicileri döndürülene kadar özel durum atılmadığından, yük isteği için özel durum işleme yi sağlasanız bile bu durum gerçekleşir. Böylece, aşağıdaki kod bulunamazsa bir `MyAssembly` yığın taşması ile sonuçlanır:  

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

- [Montaj yüklemesi için en iyi uygulamalar](../../framework/deployment/best-practices-for-assembly-loading.md)
- [Uygulama etki alanlarını kullanma](../../framework/app-domains/use.md)
