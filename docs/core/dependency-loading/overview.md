---
title: Bağımlılık yükleme - .NET Core
description: .NET Core'da yönetilen ve yönetilmeyen bağımlılık yüklemesi genel bakış
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416678"
---
# <a name="dependency-loading-in-net-core"></a>.NET Core'da bağımlılık yüklemesi

Her .NET Core uygulamasının bağımlılıkları vardır. Basit `hello world` uygulamanın bile .NET Core sınıf kitaplıklarının bölümlerine bağımlılığı vardır.

.NET Core varsayılan derleme yükleme mantığını anlamak, tipik dağıtım sorunlarını anlamave hata ayıklama konusunda yardımcı olabilir.

Bazı uygulamalarda, bağımlılıklar çalışma zamanında dinamik olarak belirlenir. Bu gibi durumlarda, yönetilen derlemelerin ve yönetilmeyen bağımlılıkların nasıl yüklendiğini anlamak çok önemlidir.

## <a name="understanding-assemblyloadcontext"></a>AssemblyLoadContext’i anlama

<xref:System.Runtime.Loader.AssemblyLoadContext> API,.NET Core yükleme tasarımının merkezindedir. [Anlama AssemblyLoadContext](understanding-assemblyloadcontext.md) makale tasarım için kavramsal bir bakış sağlar.

## <a name="loading-details"></a>Yükleme ayrıntıları

Yükleme algoritması ayrıntıları birkaç makalede kısaca ele alınmıştır:

- [Yönetilen montaj yükleme algoritması](loading-managed.md)
- [Uydu montaj yükleme algoritması](loading-resources.md)
- [Yönetilmeyen (yerel) kitaplık yükleme algoritması](loading-unmanaged.md)
- [Varsayılan sondalama](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Eklentilerle .NET Core uygulaması oluşturma

Öğretici [Eklentileri ile bir .NET Core uygulaması oluşturun](../tutorials/creating-app-with-plugin-support.md) nasıl özel bir AssemblyLoadContext oluşturmak için açıklar. Eklentinin <xref:System.Runtime.Loader.AssemblyDependencyResolver> bağımlılıklarını gidermek için a kullanır. Öğretici, eklentinin bağımlılıklarını barındırma uygulamasından doğru bir şekilde yalıtır.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama

[.NET Core makalesinde montaj yüklenebilirliğinin nasıl kullanılacağı ve hata ayıklanabilirliğinin nasıl kullanılacağı,](../../standard/assembly/unloadability.md) adım adım öğreticidir. Bir .NET Core uygulamasının nasıl yüklenir, yürütülür ve sonra nasıl boşaltılmayı gösterir. Makale de hata ayıklama ipuçları sağlar.
