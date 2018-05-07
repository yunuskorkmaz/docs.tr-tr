---
title: Windows 8'de .NET Framework 2.0'ı hedefleme
description: "F # kullanırken .NET Framework'ün daha eski sürümünü hedefleme hakkında bilgi edinin."
ms.date: 05/16/2016
ms.openlocfilehash: 9b08cced63b46778a5081d4de710991a6299fd29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="targeting-older-versions-of-net"></a>.NET hedefleme eski sürümleri

> [!NOTE]
Bu makale, en son Visual Studio ile güncel değil.  Güncelleştirilecek.

.NET Framework 2.0 hedef çalışırsanız, Visual Studio üzerinde Windows 8.1 yüklendiğinde 3.0 veya 3.5 bir F # proje aşağıdaki hata görünebilir: 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

Bu hata, aşağıdaki koşullar bileşimi altında oluştuğu bilinmektedir:


- Visual Studio Windows 8.1 üzerinde yüklü.
<br />

- Visual Studio yüklemeden önce .NET Framework 3.5 etkinleştirin alamadık.
<br />

- Projeniz .NET Framework 2.0, 3.0 veya 3.5 hedefler.
<br />

Visual Studio yüklediğinizde, .NET Framework'ün yüklü sürümleri algılar ve .NET Framework 3.5 yalnızca yüklü ve etkinse F # 2.0 çalışma zamanı yükler.


## <a name="resolving-the-error"></a>Hatayı giderme
Bu hatayı gidermek için her iki hedef .NET Framework daha yeni bir sürümü olabilir veya Windows 8.1 üzerinde .NET Framework 3.5 etkinleştirin ve sonra F # 2.0 ile Visual Studio için Kurulum programını çalıştırarak yükleyin **onarım** seçeneği.


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Windows 8.1 üzerinde .NET Framework 3.5 etkinleştirmek için

1. Üzerinde **Başlat** ekranında, girmek başlangıç **Denetim Masası**.
<br />  Bu ada girerken **Denetim Masası** simgesi görünür altında **uygulamaları** başlığı.
<br />

2. Seçin **Denetim Masası** simgesini seçin **programlar** simgesine ve ardından **kapatma Windows özelliklerini aç veya Kapat** bağlantı.
<br />

3. Olduğundan emin olun **.NET Framework 3.5 (.NET 2.0 ve 3.0 içerir)** onay kutusu seçilidir ve ardından **Tamam** düğmesi.
<br />  .NET Framework'ün isteğe bağlı bileşenler için herhangi bir alt düğüm için onay kutularını seçin gerek yoktur.
<br />  Zaten yapmadıysanız, .NET Framework 3.5 etkinleştirilir.
<br />


#### <a name="to-install-the-f-20-runtime"></a>F # 2.0 çalışma zamanını yüklemek için

1. Denetim Masası'nda seçin **programları** bağlamak ve ardından **programlar ve Özellikler** bağlantı.
<br />

2. Yüklü programlar listesinde, yüklü ve ardından Visual Studio sürümü seçin **değişiklik** düğmesi.
<br />

3. Kurulum başladıktan sonra seçin **onarım** düğmesi.
<br />  Daha fazla bilgi için bkz: [Visual Studio'yu yükleme](https://msdn.microsoft.com/library/e2h7fzkw.aspx).
<br />
## <a name="see-also"></a>Ayrıca Bkz.
[Visual F#](../index.md)
