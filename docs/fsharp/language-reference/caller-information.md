---
title: Arayan bilgileri
description: Bir yöntemden çağıran bilgileri elde etmek için çağıran bilgileri bağımsız değişken özniteliklerinin nasıl kullanılacağını açıklar.
ms.date: 11/04/2019
ms.openlocfilehash: d995b37149277b7c7d1b6217ee484d3c90a7f8b3
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976806"
---
# <a name="caller-information"></a>Arayan bilgileri

Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz. Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.

Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz. Aşağıdaki tabloda, [System. Runtime. CompilerServices](/dotnet/api/system.runtime.compilerservices) ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir:

|Öznitelik|Açıklama|Tür|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Kaynak dosyasının arayanı içeren tam yolu. Bu, derleme zamanındaki dosya yoludur.|`String`
|[Callerlinumarası](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Arayanın yöntemi veya özellik adı. Bu konunun ilerleyen kısımlarında bulunan üye adları bölümüne bakın.|`String`|

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir çağrıyı izlemek için bu öznitelikleri nasıl kullanabileceğinizi gösterir.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member _.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a>Açıklamalar

Çağıran bilgi öznitelikleri yalnızca isteğe bağlı parametrelere uygulanabilir. Çağıran bilgi öznitelikleri, derleyicinin bir arayan bilgileri özniteliğiyle donatılmış her bir isteğe bağlı parametre için uygun değeri yazmasına neden olur.

Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir. Özel durumlar için [StackTrace](/dotnet/api/system.diagnostics.stacktrace) özelliğinin sonuçlarının aksine, sonuçlar gizleme tarafından etkilenmez.

Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.

## <a name="member-names"></a>Üye adları

Üyenin adını çağrılan metoda bir `String` bağımsız değişkeni olarak belirtmekten kaçınmak için [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) özniteliğini kullanabilirsiniz. Bu tekniği kullanarak, yeniden düzenlemeyi yeniden adlandırma sorununun `String` değerleri değiştirmediğini önleyin. Bu, özellikle aşağıdaki görevler için yararlı olur:

- İzleme ve tanılama yordamlarını kullanma.
- Verileri bağlarken [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) arabirimini uygulama. Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar. [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) özniteliği olmadan, özellik adını bir sabit değer olarak belirtmeniz gerekir.

Aşağıdaki grafikte, CallerMemberName özniteliğini kullandığınızda döndürülen üye adları gösterilmektedir.

|Çağrının oluştuğu yer|Üye adı sonucu|
|-------------------|------------------|
|Yöntem, özellik veya olay|Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.|
|Oluşturucu|".ctor" dizesi|
|Statik oluşturucu|".cctor" dizesi|
|Yok edici|"Finalize" dizesi|
|Kullanıcı tanımlı işleçler veya dönüştürmeler|Üye için oluşturulan "op_Addition" gibi bir ad.|
|Öznitelik oluşturucu|Özniteliğin uygulandığı üyenin adı. Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.|
|İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)|İsteğe bağlı parametrenin varsayılan değeri.|

## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler](attributes.md)
- [Adlandırılmış bağımsız değişkenler](parameters-and-arguments.md#named-arguments)
- [İsteğe bağlı parametreler](parameters-and-arguments.md#optional-parameters)
