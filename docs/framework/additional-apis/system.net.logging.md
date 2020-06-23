---
title: Günlük sınıfı (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990422"
---
# <a name="logging-class"></a>Logging sınıfı

İzleme günlüğü işlevlerini sağlar.

```csharp
internal class Logging
```

> [!WARNING]
> Bu sınıf dahili ve doğrudan kodunuzda kullanılmamalıdır.
>
> Microsoft, bu sınıfın herhangi bir koşulda bir üretim uygulamasında kullanımını desteklemez.

## <a name="associate-method"></a>İlişkilendir yöntemi

İki nesnenin birbirleriyle ilişkilendirildiği bilgileri günlüğe kaydeder.

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `objA` <xref:System.Object>

  İle ilişkilendirilecek nesne `objB` .

- `objB` <xref:System.Object>

  İle ilişkilendirilecek nesne `objA` .

## <a name="entertracesource-object-string-string-method"></a>ENTER (TraceSource, Object, String, String) yöntemi

Bir yönteme giriş kaydeder.

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.Object>

  Metodun çağrıldığı nesne.

- `method` <xref:System.String>

  Girilen yöntem.

- `param` <xref:System.String>

  Yöntemine geçirilen parametreler.

## <a name="entertracesource-object-string-object-method"></a>ENTER (TraceSource, Object, String, Object) yöntemi

Bir yönteme giriş kaydeder.

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.Object>

  Metodun çağrıldığı nesne.

- `method` <xref:System.String>

  Girilen yöntem.

- `paramObject` <xref:System.Object>

  Yöntemine geçirilen parametreler.

## <a name="entertracesource-string-string-string-method"></a>ENTER (TraceSource, String, String, String) yöntemi

Bir yönteme giriş kaydeder.

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.String>

  Metodun çağrıldığı nesne.

- `method` <xref:System.String>

  Girilen yöntem.

- `param` <xref:System.String>

  Yöntemine geçirilen parametreler.

## <a name="entertracesource-string-string-object-method"></a>ENTER (TraceSource, String, String, Object) yöntemi

Bir yönteme giriş kaydeder.

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.String>

  Metodun çağrıldığı nesne.

- `method` <xref:System.String>

  Girilen yöntem.

- `paramObject` <xref:System.Object>

  Yöntemine geçirilen parametreler.

## <a name="entertracesource-string-string-method"></a>ENTER (TraceSource, String, String) yöntemi

Bir yönteme giriş kaydeder.

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `method` <xref:System.String>

  Girilen yöntem.

- `parameters` <xref:System.String>

  Yöntemine geçirilen parametreler.

## <a name="entertracesource-string-method"></a>ENTER (TraceSource, String) yöntemi

Bir yönteme giriş kaydeder.

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `msg` <xref:System.String>

  İzleme kaynağına kaydedilecek giriş iletisi.

## <a name="exception-method"></a>Exception Yöntemi

Bir özel durumu günlüğe kaydeder ve girintiyi geri yükler.

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.Object>

  Özel durum oluşturan yönteminin çağrıldığı nesne.

- `method` <xref:System.String>

  Özel durumu oluşturan yöntem.

- `e` <xref:System.Exception>

  Oluşturulan özel durum.

## <a name="exittracesource-object-string-object-method"></a>Exit (TraceSource, nesne, dize, nesne) yöntemi

Günlükler bir işlevden çıkış.

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.Object>

  Metodun çağrıldığı nesne.

- `method` <xref:System.String>

  Çıkılmakta olan yöntem.

- `retObject` <xref:System.Object>

  Yöntemi tarafından döndürülen değer.

## <a name="exittracesource-string-string-object-method"></a>Exit (TraceSource, dize, dize, nesne) yöntemi

Günlükler bir işlevden çıkış.

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.String>

  Metodun çağrıldığı nesne.

- `method` <xref:System.String>

  Çıkılmakta olan yöntem.

- `retObject` <xref:System.Object>

  Yöntemi tarafından döndürülen değer.

## <a name="exittracesource-object-string-string-method"></a>Exit (TraceSource, Object, String, String) yöntemi

Günlükler bir işlevden çıkış.

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.Object>

  Metodun çağrıldığı nesne.

- `method` <xref:System.String>

  Çıkılmakta olan yöntem.

- `retValue` <xref:System.String>

  Yöntemi tarafından döndürülen değer.

## <a name="exittracesource-string-string-string-method"></a>Exit (TraceSource, dize, dize, dize) yöntemi

Günlükler bir işlevden çıkış.

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `obj` <xref:System.String>

  Metodun çağrıldığı nesne.

- `method` <xref:System.String>

  Çıkılmakta olan yöntem.

- `retValue` <xref:System.String>

  Yöntemi tarafından döndürülen değer.

## <a name="exittracesource-string-string-method"></a>Exit (TraceSource, dize, dize) yöntemi

Günlükler bir işlevden çıkış.

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `method` <xref:System.String>

  Çıkılmakta olan yöntem.

- `parameters` <xref:System.String>

  Çıkılmakta olan yönteme geçirilen parametreler.

## <a name="exittracesource-string-method"></a>Exit (TraceSource, String) yöntemi

Günlükler bir işlevden çıkış.

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a>Parametreler

- `traceSource` <xref:System.Diagnostics.TraceSource>

  Olayın günlüğe kaydedilecek izleme kaynağı.

- `msg` <xref:System.String>

  İzleme kaynağına kaydedilecek çıkış iletisi.

## <a name="http-property"></a>Http özelliği

"System .net. http" izleme kaynağını alır.

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a>Özellik değeri

<xref:System.Diagnostics.TraceSource>\
"System .net. http" için izleme kaynağı veya `null` günlüğe kaydetme etkinleştirilmemişse.

## <a name="on-property"></a>On özelliği

Günlük kaydının etkin olup olmadığını gösteren bir değer alır.

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a>Özellik değeri

<xref:System.Boolean>\
`true`günlüğe kaydetme etkinse; Aksi takdirde, `false` .

## <a name="requirements"></a>Gereksinimler

**Ad alanı:**<xref:System.Net>

**Bütünleştirilmiş kod:** Sistem (System.dll)
