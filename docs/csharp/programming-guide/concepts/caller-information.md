---
title: Arayan bilgileri (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 4b2c34945b47db01b0e655f68f92e4dae7445c2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595344"
---
# <a name="caller-information-c"></a>Arayan bilgileri (C#)

Arayan Bilgisi özniteliklerini kullanarak bir yöntemin arayanı hakkında bilgi edinebilirsiniz. Kaynak kodunun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını alabilirsiniz. Bu bilgiler, tanılama araçlarının izlenmesine, oluşturulmasına ve bu araçlarda hata ayıklanmasına yardımcı olur.

Bu bilgileri elde etmek için her biri varsayılan değere sahip isteğe bağlı parametrelere uygulanan öznitelikler kullanabilirsiniz. Aşağıdaki tabloda, <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanında tanımlanan arayan bilgileri öznitelikleri listelenmektedir:

|Öznitelik|Açıklama|Tür|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Bu, derleme zamanındaki dosya yoludur.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Arayanın yöntemi veya özellik adı. Bu konunun devamındaki [üye adları](#member-names) bölümüne bakın.|`String`|

## <a name="example"></a>Örnek

Aşağıdaki örnekte, Arayanın Bilgisi özniteliklerinin nasıl kullanılacağı gösterilmiştir. `TraceMessage` Yöntemine yapılan her çağrıda, çağıran bilgileri isteğe bağlı parametrelere bağımsız değişkenler olarak değiştirilir.

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a>Açıklamalar

Her isteğe bağlı parametre için açık bir varsayılan değer belirtmeniz gerekir. İsteğe bağlı olarak belirtilmeyen parametrelere Arayan Bilgisi özniteliklerini uygulayamazsınız.

Arayan Bilgisi öznitelikleri, bir parametreyi isteğe bağlı hale getirmez. Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler.

Arayan Bilgisi değerleri, derleme zamanında Ara Dile (IL) değişmez değerler olarak verilir. Özel durumlar için <xref:System.Exception.StackTrace%2A> Özellik sonuçlarının aksine, sonuçlar gizleme tarafından etkilenmez.

Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.

### <a name="member-names"></a>Üye adları

`CallerMemberName` Özniteliği, çağrılan yönteme bir `String` bağımsız değişken olarak üye adını belirtmekten kaçınmak için kullanabilirsiniz. Bu tekniği kullanarak **yeniden düzenlemeyi yeniden adlandırma** sorunu, `String` değerleri değiştirmez. Bu, özellikle aşağıdaki görevler için yararlı olur:

- İzleme ve tanılama yordamlarını kullanma.

- Verileri bağlarken <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi uygulama. Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar. `CallerMemberName` Özniteliği olmadan, özellik adını bir sabit değer olarak belirtmeniz gerekir.

Aşağıdaki grafikte, `CallerMemberName` özniteliğini kullandığınızda döndürülen üye adları gösterilmektedir.

|Çağrının oluştuğu yer|Üye adı sonucu|
|-|-|
|Yöntem, özellik veya olay|Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.|
|Oluşturucu|".ctor" dizesi|
|Statik oluşturucu|".cctor" dizesi|
|Yok edici|"Finalize" dizesi|
|Kullanıcı tanımlı işleçler veya dönüştürmeler|Üye için oluşturulan "op_Addition" gibi bir ad.|
|Öznitelik oluşturucu|Özniteliğin uygulandığı yöntemin veya özelliğin adı. Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.|
|İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)|İsteğe bağlı parametrenin varsayılan değeri.|

## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler (C#)](./attributes/index.md)
- [Ortak öznitelikler (C#)](./attributes/common-attributes.md)
- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [Programlama kavramları (C#)](./index.md)
