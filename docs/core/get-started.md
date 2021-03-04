---
title: .NET kullanmaya başlama
description: Merhaba Dünya .NET uygulaması oluşturun.
author: adegeo
ms.author: adegeo
ms.date: 09/29/2020
ms.custom: vs-dotnet
ms.openlocfilehash: f196f5cfe914fe7ecddec61d2abf618c21968bbd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105160"
---
# <a name="get-started-with-net"></a>.NET kullanmaya başlama

Bu makalede bir "Merhaba Dünya!" oluşturma ve çalıştırma hakkında öğretilir .NET uygulaması.

.NET ' in ne olduğundan emin değilseniz, [.net tanıtımı](introduction.md)ile başlayın.

## <a name="create-an-application"></a>Uygulama oluşturma

İlk olarak, bilgisayarınıza [.NET SDK 'sını](https://dotnet.microsoft.com/download/dotnet) indirip yükleyin.

Ardından, **PowerShell**, **komut istemi** veya **Bash** gibi bir Terminal açın. `dotnet`Bir C# uygulaması oluşturmak ve çalıştırmak için aşağıdaki komutları girin:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Aşağıdaki çıktıyı görürsünüz:

```output
Hello World!
```

Tebrikler! Basit bir .NET uygulaması oluşturdunuz.

## <a name="next-steps"></a>Sonraki adımlar

Bir [adım adım öğreticiyi](../standard/get-started.md) Izleyerek veya YouTube 'da [.net 101 videolarını](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) izleyerek .NET uygulamaları geliştirmeye başlayın.
