---
title: .NET Framework için kod Çözümleyicileri
titleSuffix: ''
description: Kodunuzda sorunları bulmak ve gidermek için .NET Framework Çözümleyicileri paketindeki Çözümleyicileri nasıl kullanacağınızı öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687918"
---
# <a name="code-analysis"></a>Kod analizi

.NET Framework uygulama kodunuzda olası sorunları bulmak için kod Çözümleyicileri kullanabilirsiniz. Çözümleyiciler olası sorunları bullar ve bunlara yönelik düzeltmeler önerir.

Roslyn tabanlı kod Çözümleyicileri, kodunuzu yazarken veya bir CI yapısının parçası olarak Visual Studio 'da etkileşimli olarak çalışır. Çözümleyiciler geliştirme döngüsünün mümkün olduğunca erken eklemeniz gerekir. Kodunuzda olası sorunları daha önce bulduklarında, bunları çözmeleri daha kolay olur. Çözümleyiciler, var olan koddaki sorunları bayrak ve geliştirmeye devam ederken yeni sorunlar hakkında uyarır.

## <a name="install-and-configure-analyzers"></a>Çözümleyicileri yükleyip yapılandırma

.NET Framework Çözümleyicisi, [Microsoft. NetFramework. çözümleyiciler](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketinde dağıtılır. Bu paket, güvenlik Çözümleyicileri içeren .NET Framework API 'Lerine özgü çözümleyiciler sağlar. Paket, [Microsoft. CodeAnalysis. Fxcopçözümleyiciler paketine](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)dahildir. bu nedenle, paketi yüklerseniz, .NET Framework çözümleyicilerinin ayrı olarak yüklenmesi gerekmez.

Çözümleyicilerin çalıştırmasını istediğiniz her projeye NuGet paketini yükler. Yalnızca bir geliştiricinin projeye eklemesi gerekir. Çözümleyici paketi bir proje bağımlılığıdır ve güncelleştirilmiş çözüme sahip olduktan sonra her geliştiricinin makinesinde çalışır.

Paketi yüklemek için projeye sağ tıklayın ve "bağımlılıkları Yönet" i seçin. NuGet Gezgini 'nden "Microsoft. NetFramework. çözümleyiciler" araması yapın. Çözümünüzdeki tüm projelere en son kararlı sürümü yükler.

## <a name="use-the-analyzers"></a>Çözümleyicileri kullanma

NuGet paketi yüklendikten sonra çözümünüzü derleyin. Çözümleyici, kod tabanınızda bulduğu tüm sorunları rapor eder. Sorunlar, aşağıdaki görüntüde gösterildiği gibi Visual Studio Hata Listesi penceresinde uyarı olarak bildirilir:

![.NET Framework Çözümleyicileri tarafından bildirilen sorunlar.](./media/framework-analyzers-2.png)

Kod yazarken, kodunuzda olası bir sorunu dalgalı çizgiler görürsünüz.
Daha fazla bilgi edinmek için herhangi bir sorunun üzerine gelin ve aşağıdaki görüntüde gösterildiği gibi olası bir düzeltmeyle ilgili önerileri görün:

![Kod Çözümleyicileri tarafından bulunan sorunların etkileşimli raporu.](./media/framework-analyzers-1.png)

Daha fazla bilgi için bkz. [Visual Studio 'Da kod analizi](/visualstudio/code-quality/roslyn-analyzers-overview).

## <a name="types-of-rules"></a>Kural türleri

Çözümleyiciler çözümünüzdeki kodu ve bir ön ek ile yüzey uyarılarını inceler `CA` . Olası tüm uyarıların listesi için bkz. [kod kalitesi kuralları](../fundamentals/code-analysis/quality-rules/index.md). Bu uyarılardan yalnızca bazıları aşağıdakiler dahil .NET Framework API 'LERI için geçerlidir:

- [CA1058: Türler belirli temel türleri aşmamalıdır](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [CA2153: bozuk durum özel durumlarını yakalamayın](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [CA2229: Serileştirme oluşturucularını uygulayın](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [CA2237: ISerializable türlerini seri hale getirilebilir ile Işaretle](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [CA3075: XML 'de güvenli olmayan DTD işleme](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [CA5350: zayıf şifreleme algoritmaları kullanmayın](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [CA5351 kopuk şifreleme algoritmaları kullanma](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da kod analizi](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET SDK 'da kod analizi](../fundamentals/code-analysis/overview.md)
