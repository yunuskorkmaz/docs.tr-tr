---
title: Genelleştirme kuralları (kod analizi)
description: Kod Analizi kuralı Genelleştirme kuralları hakkında bilgi edinin
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- rules, globalization
- globalization rules
- globalization [Visual Studio], rules
- managed code analysis rules, globalization rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 83ecc52c5e20e074c6c1aed68204a574494f42d5
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589261"
---
# <a name="globalization-rules"></a>Genelleştirme kuralları

Genelleştirme kuralları, dünyaya yönelik kitaplıkları ve uygulamaları destekler.

## <a name="in-this-section"></a>Bu bölümde

|Kural|Description|
|----------|-----------------|
|[CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](ca1303.md)|Dışarıdan görülebilen bir yöntem, bir dize sabit değerini bir .NET oluşturucusuna veya yöntemine parametre olarak geçirir ve bu dize yerelleştirilebilir olmalıdır.|
|[CA1304: CultureInfo belirt](ca1304.md)|Yöntem veya Oluşturucu System.Globalization.CultureInfo parametre kabul eden aşırı yüklenmiş üye arar ve yöntem veya oluşturucu CultureInfo parametresi aşırı yükleme çağıramaz. Bir CultureInfo veya System.IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir.|
|[CA1305: IFormatProvider belirt](ca1305.md)|Yöntem veya oluşturucu System.IFormatProvider parametresini kabul eden aşırı yüklü bir veya daha fazla üye arar ve yöntem veya oluşturucu IFormatProvider parametre yüklemesini çağırmaz. Bir System.Globalization.CultureInfo veya IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir.|
|[CA1307: Daha anlaşılır olması için StringComparison belirtin](ca1307.md)|StringComparison parametresi ayarlanmamış bir yöntemi aşırı bir dize karşılaştırma işleminde kullanır.|
|[CA1308: Dizeleri büyük harfe normalleştirin](ca1308.md)|Dizeler büyük harfe normalleştirilmeli. Küçük bir karakter grubu küçük harfe dönüştürüldüğünde gidiş dönüş yapamaz.|
|[CA1309: Sıralı StringComparison kullanın](ca1309.md)|StringComparison parametresini Ordinal ya da OrdinalIgnoreCase'a ayarlayamayan dilbilimsel olmayan dize karşılaştırma işlemi. Açıkça StringComparison.Ordinal veya StringComparison.OrdinalIgnoreCase için parametre ayarıyla kodunuz genellikle hızlanır, daha doğru olur ve daha güvenilir hale gelir.|
|[CA1310: Doğruluk için StringComparison belirtin](ca1310.md)|Dize karşılaştırma işlemi, StringComparison parametresi ayarlanmamış ve varsayılan olarak kültüre özgü dize karşılaştırmayı kullanan bir yöntem aşırı yüklemesi kullanır.|
|[CA2101: P/Invoke dize bağımsız değişkenleri için sıralama belirtin](ca2101.md)|Platform çağırma üyesi kısmen güvenilen çağıranlar için izin verir, bir dize parametresine sahiptir ve dizeyi açıkça sıralamaz. Bu, olası bir güvenlik açığına neden olabilir.|
