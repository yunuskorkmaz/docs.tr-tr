---
title: 'C# Ayrılmış öznitelikler: Arayan bilgilerini izleme'
ms.date: 04/09/2020
description: Bu öznitelikler derleyiciye üye çağıran kod hakkında bilgi oluşturmasını bildirir. Ayrıntılı izleme bilgileri sağlamak için CallerFilePath, CallerLineNumber ve CallerMemberName'yi kullanıyorsunuz
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389879"
---
# <a name="reserved-attributes-determine-caller-information"></a>Ayrılmış öznitelikler: Arayan bilgilerini belirleme

Bilgi özniteliklerini kullanarak, bir yönteme arayan hakkında bilgi elde elabilirsiniz. Kaynak kodun dosya yolunu, kaynak kodundaki satır numarasını ve arayanın üye adını elde elabilirsiniz. Üye arayan bilgilerini elde etmek için isteğe bağlı parametrelere uygulanan öznitelikleri kullanırsınız. Her isteğe bağlı parametre varsayılan değer belirtir. Aşağıdaki <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> tabloda, ad alanında tanımlanan Arayan Bilgileri öznitelikleri listelenir:

|Öznitelik|Açıklama|Tür|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|Kaynak dosyasının arayanı içeren tam yolu. Tam yol derleme zamanda ki yoldur.|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|Yöntemin çağrıldığı kaynak dosyadaki satır numarası.|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|Arayanın yöntem adı veya özellik adı.|`String`|

Bu bilgiler, izleme, hata ayıklama yazmanıza ve tanılama araçları oluşturmanıza yardımcı olur. Aşağıdaki örnek, arayan bilgileri özniteliklerinin nasıl kullanılacağını gösterir. `TraceMessage` Yönteme yapılan her çağrıda, arayan bilgileri isteğe bağlı parametrelere bağımsız değişken olarak ikame edilir.

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

Her isteğe bağlı parametre için açık bir varsayılan değer belirtirsiniz. Arayan bilgi özniteliklerini isteğe bağlı olarak belirtilmeyen parametrelere uygulayamazsınız. Arayan bilgi öznitelikleri bir parametre isteğe bağlı yapmaz. Bunun yerine, bağımsız değişken atlandığında geçirilen varsayılan değeri etkilerler. Arayan bilgi değerleri derleme zamanında Ara Dile (IL) edebi olarak yayılır. <xref:System.Exception.StackTrace%2A> Özel durumlar için özelliğin sonuçlarının aksine, sonuçlar gizlemeden etkilenmez. Arayan bilgisini denetlemek veya gizlemek için isteğe bağlı bağımsız değişkenleri açıkça sağlayabilirsiniz.

### <a name="member-names"></a>Üye adları

Özniteliği, `CallerMemberName` üye adı niçin çağrılması `String` metoduna bağımsız değişken olarak belirtmemek için kullanabilirsiniz. Bu tekniği kullanarak, **Yeniden Adlandırma Değerlerini** değiştirmez `String` sorunu önlemek. Bu, özellikle aşağıdaki görevler için yararlı olur:

- İzleme ve tanılama yordamlarını kullanma.
- Verileri bağlarken <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi uygulama. Bu arabirim, bir nesnenin özelliğinin bağlama denetimine özelliğin değiştirildiğini bildirmesini ve böylece denetimin güncelleştirilmiş bilgileri görüntüleyebilmesini sağlar. `CallerMemberName` Öznitelik olmadan, özellik adını gerçek olarak belirtmeniz gerekir.

Aşağıdaki grafik, özniteliği kullandığınızda `CallerMemberName` döndürülen üye adları gösterir.

|Aramalar içinde oluşur|Üye adı sonucu|
|-|-|
|Yöntem, özellik veya olay|Yöntemin, özelliğin veya aramanın kaynaklandığı olayın adı.|
|Oluşturucu|".ctor" dizesi|
|Statik oluşturucu|".cctor" dizesi|
|Yok edici|"Finalize" dizesi|
|Kullanıcı tanımlı işleçler veya dönüştürmeler|Üye için oluşturulan "op_Addition" gibi bir ad.|
|Öznitelik oluşturucu|Özniteliğin uygulandığı yöntemin veya özelliğin adı. Öznitelik bir üye içerisindeki herhangi bir öğeyse (parametre, dönüş değeri veya genel tür parametresi gibi), bu sonuç bu öğeyle ilişkili öğenin adıdır.|
|İçeren üye yok (örneğin, derleme düzeyi veya türlere uygulanan öznitelikler)|İsteğe bağlı parametrenin varsayılan değeri.|

## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [Öznitelikler](../../../standard/attributes/index.md)
