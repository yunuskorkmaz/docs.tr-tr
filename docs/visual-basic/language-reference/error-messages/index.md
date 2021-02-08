---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic hata iletileri'
title: Visual Basic hata iletileri
titleSuffix: ''
ms.date: 10/13/2020
helpviewer_keywords:
- errors [Visual Basic]
- error messages
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 28e59a47c47ff7905dfec93b057f7cb534842b91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796073"
---
# <a name="error-messages-in-visual-basic"></a>Visual Basic hata iletileri

Bir Visual Basic uygulamasını derlerken veya çalıştırdığınızda aşağıdaki hata türleri meydana gelebilir:

- Bir uygulamayı derlerken oluşan derleme zamanı hataları.

- Bir uygulama çalışırken oluşan çalışma zamanı hataları.

Belirli bir hata giderme hakkında daha fazla bilgi için bkz. [Visual Basic programcıları Için ek kaynaklar](../../getting-started/additional-resources.md).

## <a name="run-time-errors"></a>Çalışma zamanı hataları

Visual Basic bir uygulama sistemin yürütemeyeceğini bir eylem gerçekleştirmeye çalışırsa, bir çalışma zamanı hatası oluşur ve Visual Basic bir <xref:System.Exception> nesne oluşturur. Visual Basic, ifadesini kullanarak nesneler dahil olmak üzere herhangi bir veri türünde özel hatalar oluşturabilir `Exception` `Throw` . Bir uygulama, yakalanan bir özel durumun hata numarasını ve iletisini görüntüleyerek hatayı tanımlayabilir. Bir hata yakalanmazsa, uygulama sonlanır.

Kod, çalışma zamanı hatalarını yakalayabilir ve inceleyebilir. Hata veren kodu bir blokta çevrelemek isterseniz `Try` , eşleşen bir blok içinde oluşan herhangi bir hatayı yakalayabilirsiniz `Catch` . Çalışma zamanında hataları yakalama ve kodunuzda yanıtlama hakkında daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../statements/try-catch-finally-statement.md).

## <a name="compile-time-errors"></a>Derleme zamanı hataları

Visual Basic Derleyicisi kodda bir sorunla karşılaşırsa, derleme zamanı hatası oluşur. Visual Studio Code düzenleyicisinde, bu kod satırının altında dalgalı bir çizgi göründüğünden, hataya neden olan kod satırını kolayca belirleyebilirsiniz. Dalgalı alt çizgiyi işaret ettikten veya **hata listesi** açarsanız, diğer iletileri de gösteren hata iletisi görüntülenir.

Bir tanımlayıcının dalgalı bir alt çizgi varsa ve en sağdaki karakter altında kısa bir alt çizgi görünürse, sınıf, Oluşturucu, yöntem, özellik, alan veya sabit listesi için bir saplama oluşturabilirsiniz. Daha fazla bilgi için bkz. [kullanımdan oluşturma (Visual Studio)](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).

Visual Basic derleyicisinden uyarıları çözümleyerek daha hızlı çalışan ve daha az hata içeren bir kod yazabilirsiniz. Bu uyarılar, uygulama çalıştırıldığında hatalara neden olabilecek kodu belirler. Örneğin derleyici, atanmamış bir nesne değişkeninin bir üyesini çağırmaya çalışırsanız, dönüş değerini ayarlamadan bir işlevden geri dönüş veya `Try` özel durumları yakalamak için mantığdaki hatalarla bir blok yürütmeye çalıştığınızda sizi uyarır. Bunları açma ve kapatma dahil olmak üzere uyarılar hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).
