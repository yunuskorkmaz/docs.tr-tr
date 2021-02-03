---
title: Bağımlılık yükleme-.NET Core
description: .NET Core 'da yönetilen ve yönetilmeyen bağımlılık yüklemeye genel bakış
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 2eaa01fad3913272dc90891592d0e35cd89ad2ab
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506324"
---
# <a name="dependency-loading-in-net-core"></a>.NET Core 'da bağımlılık yükleme

Her .NET Core uygulamasının bağımlılıkları vardır. Basit uygulamanın, `hello world` .NET Core sınıf kitaplıklarının bölümlerine bağımlılıklar de vardır.

.NET Core varsayılan derleme yükleme mantığını anlamak, tipik dağıtım sorunlarının anlaşılmasına ve hata ayıklamasına yardımcı olabilir.

Bazı uygulamalarda bağımlılıklar, çalışma zamanında dinamik olarak belirlenir. Bu durumlarda, yönetilen derlemelerin ve yönetilmeyen bağımlılıkların nasıl yüklendiğini anlamak önemlidir.

## <a name="understanding-assemblyloadcontext"></a>AssemblyLoadContext’i anlama

<xref:System.Runtime.Loader.AssemblyLoadContext>API, .NET Core yükleme tasarımına yönelik olarak tasarlanmıştır. [AssemblyLoadContext 'ı anlama](understanding-assemblyloadcontext.md) makalesi, tasarıma kavramsal bir genel bakış sağlar.

## <a name="loading-details"></a>Yükleme ayrıntıları

Yükleme algoritması ayrıntıları birkaç makalede kısaca ele alınmıştır:

- [Yönetilen derleme yükleme algoritması](loading-managed.md)
- [Uydu derleme yükleme algoritması](loading-resources.md)
- [Yönetilmeyen (yerel) kitaplık yükleme algoritması](loading-unmanaged.md)
- [Varsayılan yoklama](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Eklentilerle .NET Core uygulaması oluşturma

[Eklentilerle bir .NET Core uygulaması oluşturma](../tutorials/creating-app-with-plugin-support.md) öğreticisi, özel bir AssemblyLoadContext oluşturmayı açıklar. <xref:System.Runtime.Loader.AssemblyDependencyResolver>Eklentinin bağımlılıklarını çözümlemek için bir kullanır. Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru şekilde yalıtır.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama

[.NET Core makalesindeki derleme ve hata ayıklama bütünleştirilmiş kodu kullanımı](../../standard/assembly/unloadability.md) , adım adım öğreticidir. .NET Core uygulamasını yüklemeyi, çalıştırmayı ve sonra kaldırmayı gösterir. Makalede ayrıca hata ayıklama ipuçları sunulmaktadır.

## <a name="collect-detailed-assembly-loading-information"></a>Ayrıntılı derleme yükleme bilgilerini topla

[Ayrıntılı derleme yükleme bilgilerini topla](collect-details.md) makalesinde, çalışma zamanında yönetilen derleme yükleme hakkında ayrıntılı bilgilerin nasıl toplanacağı açıklanır. Çalışan bir işlemin izlemede derleme yükleyici olaylarını yakalamak için [DotNet-Trace](../diagnostics/dotnet-trace.md) aracını kullanır.
