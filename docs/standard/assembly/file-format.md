---
title: .NET derlemesi dosya biçimi
description: .NET uygulamaları ve kitaplıklarını anlatmak ve içermesi için kullanılan .NET derleme dosyası biçimi hakkında bilgi edinin.
author: richlander
ms.date: 08/20/2019
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: b4aa961c3a6f2d4fa1580ff608aaf2a40d462fa0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288517"
---
# <a name="net-assembly-file-format"></a>.NET derlemesi dosya biçimi

.NET *, .net*programlarını tamamen tanımlamakta ve içerecek şekilde kullanılan bir ikili dosya biçimi tanımlar. Derlemeler, tüm bağımlı kitaplıkların yanı sıra programların kendileri için de kullanılır. .NET programı, uygun .NET uygulamasının ötesinde bir veya daha fazla gerekli yapıt olmadan bir veya daha fazla derleme olarak yürütülebilir. İşletim sistemi API 'Leri de dahil olmak üzere yerel bağımlılıklar ayrı bir konudur ve bazı durumlarda bu biçimde (örneğin, WinRT) açıklansa da .NET derleme biçimi içinde yer alır.

> Her CLı bileşeni, bu bileşene özgü bildirimler, uygulamalar ve başvurular için meta verileri taşır. Bu nedenle, bileşene özgü meta veriler bileşen meta verileri olarak adlandırılır ve sonuçta elde edilen bileşen ECMA 335 I. 9.1, bileşenler ve derlemelerden kendi kendine açıklanmaktadır.

Biçim tam olarak belirtilmiştir ve [ECMA 335](https://www.ecma-international.org/publications/standards/Ecma-335.htm)olarak standartlaştırılmış olur. Tüm .NET derleyicileri ve çalışma zamanları bu biçimi kullanır. Belgelenmiş ve sık güncelleştirilmemiş bir ikili biçiminin varlığı, birlikte çalışabilirlik için önemli bir avantajdır (korumalı bir gereksinimdir). Biçim en son, 2005 (.NET 2,0) ' de genel türler ve işlemci mimarisine uyum sağlamak için en son bir şekilde güncelleştirildi.

Biçim CPU ve işletim sistemi belirsiz ' dir. Birçok yongaları ve CPU 'yu hedefleyen .NET uygulamalarının bir parçası olarak kullanılmıştır. Biçimin kendisi Windows herıt 'e sahip olsa da, herhangi bir işletim sisteminde uyguıtable olur. İşletim sistemi ile birlikte çalışabilirlik için en önemli seçenek, çoğu değerin küçük endian biçiminde depolanmasıdır. Makine işaretçi boyutuna özgü bir benzeşimine sahip değildir (örneğin, 32 bit, 64 bit).

.NET derleme biçimi, belirli bir programın veya kitaplığın yapısı hakkında da çok daha açıklayıcı bir addır. Bir derlemenin iç bileşenlerini, özellikle de derleme başvurularını ve tanımlı türleri ve bunların iç yapısını açıklar. Araçlar veya API 'Ler, bu bilgileri görüntüleme veya programlama kararları almak için okuyabilir ve işleyebilir.

## <a name="format"></a>Biçimlendir

.NET ikili biçimi, Windows [PE dosya](https://en.wikipedia.org/wiki/Portable_Executable) biçimini temel alır. Aslında, .NET sınıf kitaplıkları Windows PEs ile uyumlu değildir ve ilk bakışta Windows dinamik bağlantı kitaplıkları (dll 'Ler) veya uygulama yürütülebilir dosyaları (EXEs) olarak görünür. Bu, yerel yürütülebilir ikili dosyalar olarak maske oluşturabileceğiniz ve aynı işleme (örneğin, işletim sistemi yükü, PE Araçları) sahip oldukları Windows 'da çok faydalı bir özelliğidir.

![Derleme üstbilgileri](../media/assembly-format/assembly-headers.png)

ECMA 335 II. 25.1 'den derleme üst bilgileri, çalışma zamanı dosya biçiminin yapısı.

## <a name="process-the-assemblies"></a>Derlemeleri işleme

Derlemeleri işlemek için araçlar veya API 'Ler yazmak mümkündür. Derleme bilgileri, çalışma zamanında programlama kararları oluşturmayı, derlemeleri yeniden yazmayı, bir düzenleyicide API IntelliSense sağlamayı ve belge oluşturmayı sağlar. <xref:System.Reflection?displayProperty=nameWithType>, <xref:System.Reflection.MetadataLoadContext?displayProperty=nameWithType> , ve [mono. CECIL](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) , bu amaçla sık kullanılan araçların yararlı örnekleridir.
