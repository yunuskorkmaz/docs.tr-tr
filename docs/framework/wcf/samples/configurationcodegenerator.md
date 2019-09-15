---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f12fae48f1cee198aac22e6f09e616b407b4e9b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990059"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="f1a1b-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="f1a1b-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="f1a1b-103">ConfigurationCodeGenerator, özel kanal uygulamalarınızı yapılandırma sistemine sunmak için kullanabileceğiniz bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="f1a1b-104">Bu, özel kanalınızın kullanıcılarının, `NetTcpBinding` `TcpTransportBindingElement`veya kullanarak özel bir bağlama gibi sistem tarafından sağlanmış bir bağlamayı yapılandırdıkları gibi bir. config dosyası kullanarak kanalınızı yapılandırmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="f1a1b-105">Bir özel kanal yazdığınızda `BindingElement` ve bunu yeni bir veya `Binding`kullanarak programlama modelinde kullanıma sundığınızda, bir. config dosyası kullanarak `BindingElement` veya `Binding` yapılandırılabilir hale getirmek için bir sınıf kümesi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="f1a1b-106">Bu sınıfları oluşturmak ve müşterinizin deneyimini geliştirmek için ConfigurationCodeGenerator aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="f1a1b-107">Aracı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f1a1b-107">To build the tool</span></span>  
  
1. <span data-ttu-id="f1a1b-108">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f1a1b-109">Çözümün oluşturulması bir dosya oluşturur: ConfigurationCodeGenerator. exe.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="f1a1b-110">SampleRun. cmd dosyası, bu aracın [taşıma için sınıfları oluşturmak üzere nasıl kullanılacağını gösteren örnek bir komut satırına sahiptir: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="f1a1b-111">Aracı çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f1a1b-111">To run the tool</span></span>  
  
1. <span data-ttu-id="f1a1b-112">Komut isteminde, hem özel `BindingElement` bir tür hem de özel `Binding` bir tür varsa aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="f1a1b-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="f1a1b-113">Ya da yalnızca özel `BindingElement` bir tür varsa şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="f1a1b-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="f1a1b-114">Ya da yalnızca özel `Binding` bir tür varsa şunları yazın:</span><span class="sxs-lookup"><span data-stu-id="f1a1b-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="f1a1b-115">Komut için `BindingElement` üç. cs dosyası (/be: Option belirttiyseniz), standart `Binding` için beş. cs dosyası (/SB: Option belirttiyseniz) ve bir. xml dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="f1a1b-116">/İn seçeneğini kullandıysanız,. cs dosyalarından biri bağlama öğesi `BindingElementExtensionSection` için öğesini uygular.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="f1a1b-117">Bu kod, diğer `BindingElement` özel Bağlamalarınızın bağlama öğesini kullanabilmesi için yapılandırma sistemine bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="f1a1b-118">Diğer dosyalarda varsayılanlar ve sabitleri temsil eden sınıflar vardır.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="f1a1b-119">Dosyalar, varsayılan `//TODO` değerleri güncelleştirmenizi hatırlatmak için yorumlardır.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="f1a1b-120">/SB seçeneğini belirlediyseniz,. cs dosyalarından ikisi `StandardBindingElement` `StandardBindingCollectionElement` sırasıyla bir ve, yapılandırma sistemine standart bağlamayı sunan bir ve uygular.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="f1a1b-121">Diğer dosyalarda varsayılanlar ve sabitleri temsil eden sınıflar vardır.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="f1a1b-122">Dosyalar, varsayılan `//TODO` değerleri güncelleştirmenizi hatırlatmak için yorumlardır.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="f1a1b-123">/SB: seçeneğini belirlediyseniz, CodeToAddTo\<. >. cs, standart bağlamayı uygulayan sınıfa el ile eklemeniz gereken bir kod içerir.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="f1a1b-124">SampleConfig. xml dosyası, önceki 1 veya 2. adımda tanımlanan işleyicileri kaydeden yapılandırma dosyasına eklemeniz gereken yapılandırma kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f1a1b-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
