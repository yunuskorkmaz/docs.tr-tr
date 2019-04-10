---
title: Arayan bilgileri
description: Bir yöntemi arayan bilgileri almak için çağırıcı bilgisi bağımsız değişken öznitelikleri kullanmayı açıklar.
ms.date: 04/25/2017
ms.openlocfilehash: 13092df453b684d3ed4a93c842ea49c066157cb6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316160"
---
# <a name="caller-information"></a>Arayan bilgileri

Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz. Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.

Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz. Aşağıdaki tabloda tanımlanan arayan bilgisi öznitelikleri listelenmektedir [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) ad alanı:

|Öznitelik|Açıklama|Tür|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|Kaynak dosyasının arayanı içeren tam yolu. Bu, derleme zamanındaki dosya yoludur.|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|Arayanın yöntemi veya özellik adı. Bu konunun ilerleyen bölümlerinde üye adları bölümüne bakın.|`String`|

## <a name="example"></a>Örnek

Aşağıdaki örnek, çağıran izlemek için bu öznitelikler nasıl kullanacağınızı gösterir.

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member __.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a>Açıklamalar

Arayan bilgileri öznitelikleri yalnızca isteğe bağlı parametrelere uygulanabilir. Arayan bilgisi öznitelikleri arayan bilgisi özniteliği ile donatılmış her isteğe bağlı parametre için uygun değeri yazmak derleyicinin neden.

Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir. Tersine sonuçlar [StackTrace](/dotnet/api/system.diagnostics.stacktrace) özelliği için özel durumlar, sonuçlar gizlemeden etkilenmez etkilenmez.

Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.

## <a name="member-names"></a>Üye adları

Kullanabileceğiniz [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) üye adı olarak belirtmekten kaçınmak için öznitelik bir `String` çağrılan yöntemin bağımsız değişken. Bu tekniği kullanarak, yeniden adlandırma düzenlemesi değişmeyen ilişkin sorunu önleyebilirsiniz `String` değerleri. Bu, özellikle aşağıdaki görevler için yararlı olur:

* İzleme ve tanılama yordamlarını kullanma.
* Uygulama [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) veri bağlama sırasında arabirim. Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar. Olmadan [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) öznitelik, özellik adını değişmez değer olarak belirtmeniz gerekir.

Aşağıdaki grafik üyesi CallerMemberName özniteliğini kullandığınızda döndürülen adlarını gösterir.

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
