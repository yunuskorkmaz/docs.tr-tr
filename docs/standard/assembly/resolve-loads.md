---
title: Derleme yüklerini çözme
description: Bu makalede .NET AppDomain. AssemblyResolve olayı açıklanır. Bu olayı, derleme yüklemesi üzerinde denetim gerektiren uygulamalar için kullanın.
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
ms.openlocfilehash: 36f36b60a3a113c6b020cc1042c786c4091e567b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378676"
---
# <a name="resolve-assembly-loads"></a>Derleme yüklerini çözme
.NET, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> derleme yüklemesi üzerinde daha fazla denetim gerektiren uygulamalar için olayı sağlar. Uygulamanız, bu olayı işleyerek, yük bağlamına normal yoklama yollarının dışından bir derleme yükleyebilir, kaç tane derleme sürümünden hangilerinin yükleneceğini seçebilir, dinamik bir derlemeyi yayarak ve bu şekilde devam edebilir. Bu konu, olayı işlemeye yönelik rehberlik sağlar <xref:System.AppDomain.AssemblyResolve> .  
  
> [!NOTE]
> Yalnızca yansıma bağlamındaki derleme yüklerini çözümlemek için, <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> bunun yerine olayını kullanın.  
  
## <a name="how-the-assemblyresolve-event-works"></a>AssemblyResolve olayı nasıl kullanılır?  
 Olay için bir işleyici kaydettiğinizde <xref:System.AppDomain.AssemblyResolve> , çalışma zamanı bir derlemeye ada göre bağlama başarısız olduğunda işleyici çağrılır. Örneğin, aşağıdaki yöntemleri kullanıcı kodundan çağırmak olayın oluşturulmasına neden olabilir <xref:System.AppDomain.AssemblyResolve> :  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> İlk bağımsız değişkeni, yüklenecek derlemenin görünen adını temsil eden bir dize olan bir yöntem aşırı yüklemesi veya yöntem aşırı yüklemesi (yani, özelliği tarafından döndürülen dize <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> ).  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> İlk bağımsız değişkeni yüklenecek derlemeyi tanımlayan bir nesne olan bir yöntem aşırı yüklemesi veya yöntem aşırı yüklemesi <xref:System.Reflection.AssemblyName> .  
  
- Bir <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntem aşırı yüklemesi.  
  
- <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType>Başka bir <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> uygulama etki alanındaki bir nesneyi örnekleyen bir veya yöntem aşırı yüklemesi.  
  
### <a name="what-the-event-handler-does"></a>Olay işleyicisinin yaptığı  
 Olay işleyicisi, <xref:System.AppDomain.AssemblyResolve> özelliğindeki, yüklenecek derlemenin görünen adını alır <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> . İşleyici derleme adını tanımıyorsa, `null` (C#), `Nothing` (Visual Basic) veya `nullptr` (Visual C++) döndürür.  
  
 İşleyici derleme adını tanırsa, isteği karşılayan bir derlemeyi yükleyebilir ve döndürebilir. Aşağıdaki listede bazı örnek senaryolar açıklanmaktadır.  
  
- İşleyici derlemenin bir sürümünün konumunu biliyorsa, veya yöntemini kullanarak derlemeyi yükleyebilir <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> ve başarılı olursa yüklenen derlemeyi döndürebilir.  
  
- İşleyicinin bayt dizileri olarak depolanan derlemelerin bir veritabanına erişimi varsa, bir bayt dizisi alan aşırı yüklerden birini kullanarak bir bayt dizisi yükleyebilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> .  
  
- İşleyici dinamik bir derleme üretebilir ve döndürebilir.  
  
> [!NOTE]
> İşleyici, derlemeyi yük bağlamı içine, yük bağlamına veya Bağlamsız olarak yüklemesi gerekir. İşleyici, veya yöntemini kullanarak derlemeyi yalnızca yansıma bağlamına yüklerse, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> olayı oluşturan yükleme girişimi <xref:System.AppDomain.AssemblyResolve> başarısız olur.  
  
 Bu, uygun bir derlemeyi döndürecek olay işleyicisinin sorumluluğundadır. İşleyici, özellik değerini oluşturucuya geçirerek, istenen derlemenin görünen adını ayrıştırtırabilir <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> . .NET Framework 4 ' ten başlayarak, işleyici, <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> geçerli isteğin başka bir derlemenin bağımlılığı olup olmadığını bulmak için özelliğini kullanabilir. Bu bilgiler, bağımlılığı karşılayan bir derlemeyi belirlemesine yardımcı olabilir.  
  
 Olay işleyicisi derlemenin farklı bir sürümünü istenen sürümden döndürebilir.  
  
 Çoğu durumda, işleyici tarafından döndürülen derleme, işleyicinin onu içine yüklediği bağlamdan bağımsız olarak yükleme bağlamında görünür. Örneğin, işleyici <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> bir derlemeyi yük-from bağlamına yüklemek için yöntemini kullanıyorsa, işleyici onu döndürdüğünde, derleme yükleme bağlamında görüntülenir. Ancak, aşağıdaki örnekte, işleyici onu döndürdüğünde derleme bağlam olmadan görünür:  
  
- İşleyici bağlamı olmayan bir derlemeyi yükler.  
  
- <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>Özellik null değil.  
  
- İstekte bulunan derleme (diğer bir deyişle, özelliği tarafından döndürülen derleme), <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> bağlamı olmadan yükleniydi.  
  
 Bağlamlar hakkında bilgi için bkz <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> . yöntem aşırı yüklemesi.  
  
 Aynı derlemenin birden çok sürümü aynı uygulama etki alanına yüklenebilir. Tür atama sorunlarına yol açabildiğinden bu uygulama önerilmez. Bkz. [derleme yüklemesi Için en iyi uygulamalar](../../framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Olay işleyicisinin yapması gereken  
Olayı işlemeye yönelik birincil kural, <xref:System.AppDomain.AssemblyResolve> tanımadığınız bir derlemeyi döndürmeye çalışmayın. İşleyiciyi yazdığınızda hangi derlemelerin olay oluşturulmasına neden olabileceğini bilmeniz gerekir. İşleyiciniz diğer derlemeler için null değer döndürmelidir.  

> [!IMPORTANT]
> .NET Framework 4 ' ten başlayarak, <xref:System.AppDomain.AssemblyResolve> etkinlik uydu derlemeleri için oluşturulur. Bu değişiklik, işleyici tüm derleme yükleme isteklerini çözümlemeye çalışırsa .NET Framework önceki bir sürümü için yazılmış bir olay işleyicisini etkiler. Tanımadığı derlemeleri yoksaymayan olay işleyicileri bu değişiklikten etkilenmez: null döndürür ve normal geri dönüş mekanizmaları izlenir.  

Bir derlemeyi yüklerken olay işleyicisi, <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> olayın yinelemeli olarak oluşturulmasına neden olabilecek bir veya yöntem aşırı yüklerini kullanmamalıdır <xref:System.AppDomain.AssemblyResolve> , çünkü bu bir yığın taşmasına yol açabilir. (Bu konunun önceki kısımlarında sunulan listeye bakın.) Tüm olay işleyicileri döndürülünceye kadar hiçbir özel durum oluşturulmadığından, yükleme isteği için özel durum işleme sağlıyorsanız bile bu durum oluşur. Bu nedenle, aşağıdaki kod, bulunmazsa bir yığın taşmasına neden `MyAssembly` olur:  

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
