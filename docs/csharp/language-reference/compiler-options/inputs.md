---
description: Derleme için giriş dosyalarını denetlemek için C# derleyici seçenekleri. Bu seçenekler derleyicinin bağımlı derlemelerden ve modüllerden meta verileri nasıl okuduğunu belirtir.
title: C# derleyici seçenekleri-giriş dosyası seçenekleri
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- References compiler option [C#]
- AddModules compiler option [C#]
- EmbedInteropTypes compiler option [C#]
ms.openlocfilehash: 819e2322720782b94bd744e00c602221f023c0d8
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482949"
---
# <a name="c-compiler-options-that-specify-inputs"></a>Girişleri belirten C# derleyici seçenekleri

Aşağıdaki seçenekler derleyici girişlerini denetler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski *csc.exe* sözdizimi içinde gösterilir `code style` .

-   /  Başvurular `-reference` veya `-references` : belirtilen derleme dosyası veya dosyalarından meta verilere başvur.
- **AddModules**  /  `-addmodule` : bir modül ekleyin ( `target:module` Bu derlemeye ile oluşturulur.)
- **EmbedInteropTypes**  /  `-link` : belirtilen birlikte çalışma derleme dosyalarından meta verileri katıştır.

## <a name="references"></a>Başvurular

**Başvurular** seçeneği derleyicinin belirtilen dosyadaki [ortak](../keywords/public.md) tür bilgilerini geçerli projeye almasına, belirtilen derleme dosyalarından meta verilere başvurmasını sağlar.

```xml
<Reference Include="filename" />
```

 `filename` , bir derleme bildirimi içeren bir dosyanın adıdır. Birden fazla dosyayı içeri aktarmak için her bir dosya için ayrı bir **başvuru** öğesi ekleyin. **Başvuru** öğesinin alt öğesi olarak bir diğer ad tanımlayabilirsiniz:

```xml
<Reference Include="filename.dll">
  <Aliases>LS</Aliases>
</Reference>
```

Önceki örnekte, `LS` *filename.dll* derlemedeki tüm ad alanlarını içeren bir kök ad alanını temsil eden geçerli C# tanımlayıcısıdır. İçeri aktardığınız dosyaların bir bildirim içermesi gerekir. Bir veya daha fazla derleme başvurularınızın bulunduğu dizini belirtmek için [**Additionalbpaths**](advanced.md#additionallibpaths) kullanın. [**Additionalpaths**](advanced.md#additionallibpaths) konusu Ayrıca derleyicinin derlemeleri arayacağı dizinleri de tartışır. Derleyicinin bir derlemede değil bir derlemede bir tür tanımasını sağlamak için, türün bir örneğini tanımlayarak yapabileceğiniz, türü çözümlemeye zorlanmalıdır. Derleyici için bir derlemede tür adlarını çözümlemek için başka yollar vardır: Örneğin, derlemedeki bir türden kalýtýmla, tür adı daha sonra derleyici tarafından tanınacaktır. Bazen aynı bileşenin iki farklı sürümüne tek bir derlemede başvurulmasý gerekir. Bunu yapmak için, iki Dosya arasında ayrım yapmak üzere her bir dosya için **Başvurular** öğesindeki **diğer adlar** öğesini kullanın. Bu diğer ad, bileşen adı için bir niteleyici olarak kullanılacak ve dosyalardan birindeki bileşene çözümlencektir.

> [!NOTE]
> Visual Studio 'da **Başvuru Ekle** komutunu kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: başvuru Yöneticisi 'Ni kullanarak başvuru ekleme veya kaldırma](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

## <a name="addmodules"></a>AddModules

Bu seçenek, geçerli derlemeye anahtarla oluşturulmuş bir modül ekler `<TargetType>module</TargetType>` :

```xml
<AddModule Include=file1 />
<AddModule Include=file2 />
```

Burada `file` , `file2` meta veri içeren çıkış dosyalarıdır. Dosya, bütünleştirilmiş kod bildirimi içeremez. Birden fazla dosyayı içeri aktarmak için, dosya adlarını virgülle veya noktalı virgülle ayırın. **AddModules** ile eklenen tüm modüller, çalışma zamanında çıkış dosyası ile aynı dizinde olmalıdır. Diğer bir deyişle, derleme zamanında herhangi bir dizinde bir modül belirtebilirsiniz, ancak modülün çalışma zamanında uygulama dizininde olması gerekir. Modül, çalışma zamanında uygulama dizininde değilse, bir alırsınız <xref:System.TypeLoadException> . `file` bütünleştirilmiş kod içeremez. Örneğin, çıkış dosyası **modülün** [**TargetType**](output.md#targettype) seçeneğiyle oluşturulduysa, meta verileri **AddModules** ile içeri aktarılabilir.

Çıkış dosyası **Modül** dışında bir [**TargetType**](output.md#targettype) seçeneği ile oluşturulduysa, meta verileri **AddModules** ile içeri aktarılamaz, ancak [**References**](#references) seçeneğiyle içeri aktarılabilecek.

## <a name="embedinteroptypes"></a>EmbedInteropTypes

Derleyicinin, belirtilen derlemelerdeki COM tür bilgilerini şu anda derlediğiniz projede kullanılabilir hale getirmesine neden olur.

```xml
<References>
  <EmbedInteropTypes>file1;file2;file3</EmbedInteropTypes>
</References>
```

Burada  `file1;file2;file3` , derleme dosyası adlarının noktalı virgülle ayrılmış listesidir. Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri içine alın. **EmbedInteropTypes** seçeneği, gömülü tür bilgilerine sahip bir uygulamayı dağıtmanıza olanak sağlar. Uygulama daha sonra, çalışma zamanı derlemesine bir başvuruya gerek duymadan gömülü tür bilgilerini uygulayan bir çalışma zamanı derlemesinde türleri kullanabilir. Çalışma zamanı derlemesinin çeşitli sürümleri yayımlanıyorsa, katıştırılmış tür bilgilerini içeren uygulama, yeniden derlenmesi gerekmeden çeşitli sürümlerle çalışabilir. Bir örnek için bkz. [Izlenecek yol: yönetilen derlemelerden tür ekleme](../../../standard/assembly/embed-types-visual-studio.md).

**EmbedInteropTypes** seçeneğinin KULLANıLMASı özellikle com birlikte çalışabilirliğine çalışırken yararlıdır. Uygulamanızın artık hedef bilgisayarda bir birincil birlikte çalışma derlemesi (PIA) gerektirmemesi için COM türlerini katıştırabilirsiniz. **EmbedInteropTypes** seçeneği, derleyicinin başvurulan birlikte çalışma derlemesindeki com tür bilgilerini elde edilen derlenmiş koda eklemesini sağlar. COM türü, CLSID (GUID) değeri tarafından tanımlanır. Sonuç olarak, uygulamanız aynı CLSID değerleriyle aynı COM türlerini yükleyen bir hedef bilgisayarda çalışabilir. Microsoft Office otomatikleştiren uygulamalar iyi bir örnektir. Office gibi uygulamalar genellikle farklı sürümlerde aynı CLSID değerini tutacağından, uygulamanız başvurulan COM türlerini, .NET Framework 4 veya üzeri hedef bilgisayara yüklendiği sürece ve uygulamanız başvurulan COM türlerine dahil olan yöntemleri, özellikleri veya olayları kullandığında kullanabilirsiniz. **EmbedInteropTypes** seçeneği yalnızca arayüzleri, yapıları ve temsilcileri katıştırır. COM sınıfları ekleme desteklenmiyor.

> [!NOTE]
> Kodunuzda gömülü bir COM türünün örneğini oluşturduğunuzda, uygun arabirimi kullanarak örneği oluşturmanız gerekir. CoClass kullanarak gömülü COM türünün bir örneğini oluşturma girişimi hataya neden olur.

[**References**](#references) derleyici seçeneğinde olduğu gibi, **EmbedInteropTypes** derleyici seçeneği sık kullanılan .NET derlemelerine başvuran Csc. rsp yanıt dosyasını kullanır. Derleyicinin Csc. rsp dosyasını kullanmasını istemiyorsanız [**noconfig**](miscellaneous.md#noconfig) derleyici seçeneğini kullanın.

[!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]

Türü bir birlikte çalışma derlemesinden gömülü olan genel bir parametreye sahip türler, bu tür bir dış derlemeden ise kullanılamaz. Bu kısıtlama, arabirimler için geçerlidir. Örneğin, <xref:Microsoft.Office.Interop.Excel.Range> derlemede tanımlanan arabirimi göz önünde bulundurun <xref:Microsoft.Office.Interop.Excel> . Bir kitaplık, birlikte çalışma türlerini derlemeden katıştırır <xref:Microsoft.Office.Interop.Excel> ve türü arabirim olan bir parametreye sahip genel bir tür döndüren bir yöntemi ortaya koyar <xref:Microsoft.Office.Interop.Excel.Range> , bu yöntem, aşağıdaki kod örneğinde gösterildiği gibi genel bir arabirim döndürmelidir.

[!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs)]

Aşağıdaki örnekte, istemci kodu <xref:System.Collections.IList> hata olmadan genel arabirimi döndüren yöntemi çağırabilir.

[!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]
