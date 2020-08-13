---
title: ControlBuilderInterceptor sınıfı
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 0cd7409deb9cb84783cfa70600999fa4b2a2d2e2
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187992"
---
# <a name="controlbuilderinterceptor-class"></a>ControlBuilderInterceptor sınıfı

`ControlBuilderInterceptor`Sınıfı, derleme işleminin özelleştirilme veya kontrollü olmasını sağlar.

## <a name="syntax"></a>Syntax

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> `ControlBuilderInterceptor`Sınıfı dahili ve doğrudan kodunuzda kullanılması amaçlıyordu.
>
> Açıklamalar bölümünde açıklandığı gibi, bu türün varlığı, yakacının tür desteğinin mevcut olup olmadığını tespit etmek için denetlenebilir. Microsoft, herhangi bir koşulda bu sınıfın başka bir kullanımını bir üretim uygulamasında desteklemez.

## <a name="remarks"></a>Açıklamalar

.NET Framework 2,0 ve .NET Framework 3,5 ' de, [ağustos 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) güncelleştirme, derleme işlemini özelleştirmek veya denetlemek için bir dinleyici türü kullanma desteği eklemiştir. <xref:System.Type.GetType?displayProperty=nameWithType> `ControlBuilderInterceptor` Aşağıdaki kodda gösterildiği gibi, türün varlığını denetlemek için kullanarak bu desteğin mevcut olup olmadığını belirleyebilirsiniz.

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

Dönüş değeri null değilse, şifre veren desteği vardır. Dönüş değeri ise `null` veya bir özel durum oluşturulursa, ağustos 2020 güncelleştirmeleri yüklenmemiştir ve şifre oluşturma desteği yoktur.

Eğer şifre işleme desteği varsa, .NET Framework sonraki sürümlerinde tam olarak aynı şekilde, derleme işlemiyle etkileşim kuracak bir dinleyici türü yazabilir ve kaydedebilirsiniz <xref:System.Web.Compilation.ControlBuilderInterceptor> . .NET Framework 2,0 ve .NET Framework 3,5 ' de, yakalayıcısı türü aşağıdaki gereksinimleri karşılayan herhangi bir sınıf olabilir:

* Ortak, parametresiz bir oluşturucuya sahiptir.
* , `PreControlBuilderInit` `OnProcessGeneratedCode` <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> Daha sonraki .NET Framework sürümlerde bulunan ve yöntemleriyle aynı imzaya ve semantiğe sahip olan ve adlı ortak, statik olmayan yöntemlere sahiptir.

`aspnet:20ControlBuilderInterceptor`ASP.NET uygulama ayarları () içindeki anahtarı kullanarak yakalayıcıyı türünü kaydedin `<appSettings>` . Bu uygulama ayarı bilgisayarınızda veya uygulama *web.config* dosyanızda listelenmelidir. Onun derleme nitelikli tür adını kullanarak yakalayıcıyı türünü belirtin. Aşağıdaki örnek, adlı bir yakalayıcısı türünün nasıl kaydedileceği gösterilmektedir `Fabrikam.Interceptor` .

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>
```

Bir türün derleme nitelikli adını almak için <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi özelliğini kullanın.

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

Şifre işleme desteği mevcut olduğunda, derleme işlemi yukarıda açıklanan şekilde listelenen türle etkileşime girer. Yakalayıcıyı destekliyorsa, uygulama ayarı yok sayılır ve etkisizdir.

## <a name="requirements"></a>Gereksinimler

**Ad alanı:** System. Web. Compilation

**Bütünleştirilmiş kod:** System. Web (System.Web.dll)

**.NET Framework sürümleri:** 3,5, 2,0
